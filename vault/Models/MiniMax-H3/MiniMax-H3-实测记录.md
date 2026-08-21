---
title: MiniMax H3 实测记录
topic: minimax-h3-benchmarks
type: experiment-log
status: active
last_verified: 2026-08-21
cssclasses:
  - learning-page
  - experiment-log
---

# MiniMax H3 实测记录

> [!lead]
> 本页只记录**真实运行结果**，不把教程或社区说法当成已经验证。基础知识见 [[MiniMax-H3|MiniMax H3]]，性能方案见 [[MiniMax-H3-加速与优化|加速与优化]]。

> [!summary] 当前状态
> <span class="ll-badge is-test">等待首轮基线</span> FL2VA I2V 与 Ref2VA 多参考都还没有形成统一 RH / RTX 4090 实测数据。
>
> 当前最重要的不是测试更多组合，而是先建立**可复现基线**。

## 01 · 记录原则

每次测试尽量只改变一个变量，并记录足够的信息，方便后续复现和横向比较。

| 分类 | 必须记录 |
| --- | --- |
| 环境 | 日期 · RH / 本地 · GPU · ComfyUI 版本 |
| 模型 | 模式 · FL2VA / Ref2VA 具体文件 · 优化方案 |
| 输入 | Prompt · Seed · 图片 / 视频 / 音频数量与用途 |
| 生成 | 分辨率 · 帧数 / 时长 · Steps |
| 性能 | 峰值 / 大致显存 · 单次完整生成时间 |
| 结果 | 成功 / 失败 · 画质 · 动作 · 参考一致性 · 异常 / 修复 |

> [!meta] 对比测试的最低要求
> Prompt、Seed、分辨率、帧数 / 时长和参考素材尽量固定。否则速度或画质变化无法可靠归因到某个模型或优化方案。

## 02 · 首轮测试矩阵

> [!grid-2]
>
> > [!card] FL2VA · I2V
> > <span class="ll-badge is-test">待实测</span>
> >
> > **基线**
> > - [ ] 官方 FL2VA 主模型
> > - [ ] 不开 Turbo
> > - [ ] 不开 Cache
> > - [ ] 中等分辨率一组
> > - [ ] 接近 0.98 MP 一组
> >
> > **加速对比**
> > - [ ] SageAttention
> > - [ ] FL2VA 8-step Turbo
> > - [ ] SageAttention + 8-step Turbo
>
> > [!card] Ref2VA · 多参考
> > <span class="ll-badge is-test">待实测</span>
> >
> > **基线**
> > - [ ] 1 张人物参考图
> > - [ ] 人物 + 服装 + 场景多参考
> > - [ ] 记录 `ref_image_size`
> > - [ ] 比较参考数量对显存 / 速度 / 一致性的影响
> >
> > **视频 / 音频**
> > - [ ] 参考视频迁移动作
> > - [ ] 参考视频迁移运镜
> > - [ ] 音频参考与人物绑定

## 03 · Turbo / 非 Turbo 对比

| 日期 | 模式 | 分辨率 | 时长 | Steps | 优化 | 生成时间 | 结果 |
| --- | --- | --- | --- | ---: | --- | --- | --- |
| 待测试 | | | | | | | |

> [!resource] 对应优化方案说明
> [[MiniMax-H3-加速与优化#06 · 实测顺序|查看加速与优化页的测试顺序 →]]

## 04 · 失败案例

> [!meta] 什么时候单独拆“故障排查”页？
> 先在这里积累至少 3 个真实失败案例。只有当失败模式开始重复、能够形成稳定分类时，再拆独立故障排查页。

> [!grid-3]
>
> > [!card] Case 01
> > <span class="ll-badge is-test">待记录</span>
> >
> > **现象**：待记录  
> > **条件**：待记录  
> > **原因判断**：待记录  
> > **修复**：待记录  
> > **是否复现**：待记录
>
> > [!card] Case 02
> > <span class="ll-badge is-test">待记录</span>
> >
> > **现象**：待记录  
> > **条件**：待记录  
> > **原因判断**：待记录  
> > **修复**：待记录  
> > **是否复现**：待记录
>
> > [!card] Case 03
> > <span class="ll-badge is-test">待记录</span>
> >
> > **现象**：待记录  
> > **条件**：待记录  
> > **原因判断**：待记录  
> > **修复**：待记录  
> > **是否复现**：待记录

## 05 · 当前未验证结论

> [!risk] 以下内容仍然只是教程 / 社区信息
> - SageAttention `1.3x+` 的实际收益。
> - Sol-Attn 的质量损失与兼容性。
> - Sage + Sol-Attn 是否值得同时启用。
> - 各类 8-step / 4-step Turbo LoRA 的真实画质差异。
> - EasyCache / LazyCache / TeaCache / MagCache / FirstBlockCache / Spectrum 的稳定性与质量损失。
> - Hybrid FL2VA / Ref2VA 模型的实际价值。

实测完成后，把**稳定结论**回写到对应主说明书或附页；原始测试数据继续保留在本页，避免知识页和实验记录相互污染。
