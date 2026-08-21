---
title: MiniMax H3 加速与优化
topic: minimax-h3-optimization
type: model-guide
status: learning
last_verified: 2026-08-21
cssclasses:
  - learning-page
  - model-guide
---

# MiniMax H3 加速与优化

> [!lead]
> H3 的加速方案可以分为 **Attention / Turbo LoRA / Cache & Prediction** 三条路线。本页负责回答“有哪些方案、它们是什么关系、当前先测什么”；真实速度、显存和画质结果统一进入 [[MiniMax-H3-实测记录|实测记录]]。

> [!summary] 当前判断
> <span class="ll-badge is-priority">当前优先</span> **Attention + 成熟 Turbo LoRA**
>
> Cache / Prediction 暂不作为默认方案；Hybrid Model 只保留为实验性社区资源。
>
> <small class="ll-note">状态说明：本页大多数性能描述来自 2026-08-21 教程笔记，尚未完成 RH / RTX 4090 的统一基线实测。教程结论与项目实测必须分开记录。</small>

## 01 · 三条加速路线

> [!grid-3]
>
> > [!card] Attention
> > <span class="ll-badge is-priority">优先级 A</span>
> >
> > **降低注意力计算成本**
> >
> > SageAttention · Sol-Attn
> >
> > <small class="ll-note">适合作为第一层优化：不改变 H3 的主模型路线，先验证单独开启的收益。</small>
>
> > [!card] Turbo / 蒸馏 LoRA
> > <span class="ll-badge is-priority">优先级 A</span>
> >
> > **把高 Steps 压缩到 8 / 4 步等**
> >
> > larryvrh · drbaph · Abiray · LightX2V
> >
> > <small class="ll-note">需要关注 FL2VA / Ref2VA 对应关系、原生兼容性，以及速度换来的画质变化。</small>
>
> > [!card] Cache / Prediction
> > <span class="ll-badge is-source">低优先级</span>
> >
> > **跳过或预测部分计算**
> >
> > EasyCache · TeaCache · Spectrum 等
> >
> > <small class="ll-note">教程评价中稳定性和画质风险更高，放在 Attention / Turbo 之后再测。</small>

## 02 · Attention

> [!grid-2]
>
> > [!card] SageAttention
> > <span class="ll-badge is-source">教程记录</span><span class="ll-badge is-test">待实测</span>
> >
> > <p class="ll-metric">≈ 1.3×+</p>
> >
> > **接入方式**
> > - 全局：`--use-sage-attention`
> > - 节点级：通过 KJNodes 等节点给特定模型应用优化补丁
> >
> > **当前定位**  
> > 第一批基线优化方案，优先单独测试。
>
> > [!card] Sol-Attn
> > <span class="ll-badge is-source">教程记录</span><span class="ll-badge is-test">待实测</span>
> >
> > <p class="ll-metric">较小质量损失*</p>
> >
> > **接入方式**  
> > 教程记录可通过 `ComfyUI-SolAttn_triton` 一类插件使用。
> >
> > **组合关系**  
> > 教程记录可与 SageAttention 同时开启。
> >
> > <small class="ll-note">*“质量损失较小”是教程评价，不是当前项目实测结果。</small>

> [!meta] 为什么不直接把 Sage + Sol 作为默认组合？
> “能够同时开启”只说明教程记录中的兼容路径，不代表叠加后的速度 / 画质收益一定优于单独开启。实测时先分开建立基线，再判断组合是否值得保留。

## 03 · Turbo / 蒸馏 LoRA

这组方案的重点不是记住四个作者名，而是先看清它们之间的**路线关系与 ComfyUI 接入方式**。

| 方案 | 与其它方案的关系 | ComfyUI 接入 | 当前定位 |
| --- | --- | --- | --- |
| **larryvrh** | FL2VA 蒸馏 / 加速路线 | 教程记录：原生不直接支持，需专用插件 | 上游路线 |
| **drbaph** | 基于 larryvrh | 教程记录：原生兼容 | 兼容实现 |
| **Abiray** | 基于 larryvrh | 教程记录：原生兼容 | 兼容实现 |
| **LightX2V** | 社区常见加速 LoRA 来源 | 教程记录：原生兼容 | FL2VA 8 / 4 步、Ref2VA 4 步均有对应路线 |

> [!summary] 当前测试优先级
> **先测 LightX2V，再决定是否继续展开 larryvrh 系列。**
>
> 原因不是先认定 LightX2V 质量最好，而是教程笔记里同时给出了 FL2VA 8 / 4 步、Ref2VA 4 步和 ComfyUI 原生兼容信息，适合先做统一对比基线。

> [!resource] Turbo LoRA 下载与模型对应
> [[MiniMax-H3#Turbo LoRA（可选）|查看 MiniMax H3 主说明书中的 Turbo LoRA →]]
>
> <small class="ll-note">LoRA 必须跟当前 FL2VA / Ref2VA 主模型路线对应，不默认跨路线混用。</small>

## 04 · Cache / Prediction

<div class="ll-chip-row">
  <span class="ll-chip">EasyCache</span>
  <span class="ll-chip">LazyCache</span>
  <span class="ll-chip">TeaCache</span>
  <span class="ll-chip">MagCache</span>
  <span class="ll-chip">FirstBlockCache</span>
  <span class="ll-chip">Spectrum</span>
</div>

> [!risk] 当前策略 · 不作为默认加速
> 教程评价中，这一类方案的**稳定性相对更差、质量损失更明显**。另外还记录了方案间冲突：例如同时使用 EasyCache + Spectrum 时，后者可能无法正常发挥作用。
>
> 因此当前顺序是：**Attention → Turbo LoRA → 组合验证 → 最后再单独测试 Cache。**

<small class="ll-note">这里保留方案名称，是为了后续识别与实测；在没有真实数据前，不再为每个 Cache 单独扩写一段介绍。</small>

## 05 · Hybrid Model

> [!resource] FL2VA / Ref2VA Hybrid · 社区资源
> **smhfacct / Minimax-H3-fl2va-ref2va-hybrid-models**
>
> [打开 Hugging Face ↗](https://huggingface.co/smhfacct/Minimax-H3-fl2va-ref2va-hybrid-models)
>
> <span class="ll-badge is-source">社区方案</span><span class="ll-badge is-test">待验证</span>
>
> <small class="ll-note">当前只作为实验资源保留，不替代官方 FL2VA / Ref2VA 主模型，也不进入默认推荐路线。</small>

## 06 · 实测顺序

为了能看出每一种优化到底带来了什么，测试时只逐层增加变量。

| 阶段 | 组合 | 目的 |
| ---: | --- | --- |
| **01** | 官方主模型 + 原始 Steps | 建立速度 / 画质基线 |
| **02** | + SageAttention | 单独确认 Attention 收益 |
| **03** | 对应 Turbo LoRA | 单独确认减少 Steps 的收益与损失 |
| **04** | SageAttention + Turbo | 判断两种主力方案是否值得叠加 |
| **05** | Sol-Attn | 再评估单独 / 组合价值 |
| **06** | Cache 类 | 最后测试高风险优化 |

> [!meta] 固定变量
> 每组对比尽量固定 **Prompt / Seed / 分辨率 / 帧数或时长 / 参考素材**。否则速度或画质变化无法可靠归因到某一种优化。

> [!resource] 实测数据不在本页重复维护
> [[MiniMax-H3-实测记录|打开 MiniMax H3 实测记录 →]]
>
> <small class="ll-note">这里保留“怎么选、按什么顺序测”；显存、生成时间、失败案例和最终结论统一维护在实测页。</small>
