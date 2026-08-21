---
title: MiniMax H3 提示词
topic: minimax-h3-prompting
type: model-guide
status: learning
last_verified: 2026-08-21
cssclasses:
  - learning-page
  - model-guide
---

# MiniMax H3 提示词

> [!lead]
> 本页负责 H3 的提示词结构、镜头、声音和参考素材写法。主模型、文件、模式和分辨率见 [[MiniMax-H3|MiniMax H3]]；完整 Agent 原始指令单独保存在 `resources/`。

> [!summary] 先记住 3 条
> **先选模式**：Base 与 Ref2VA 的结构不同。  
> **写变化**：描述发生什么、镜头怎么动、光线和声音怎么变，而不是重复静态画面。  
> **守时长**：镜头时间戳必须落在目标视频时长内。

## 01 · 先判断模式

> [!grid-2]
>
> > [!card] Base · T2V / I2V / FL2V / L2V
> > <span class="ll-badge is-priority">基础模式</span>
> >
> > **3 个核心字段**
> >
> > 1. `integrated_multimodal_description`
> > 2. `overall_soundscape`
> > 3. `non_diegetic_music`
> >
> > 必要时追加 `Do not include`。
> >
> > <small class="ll-note">I2V / FL2V / L2V 还需要先写参考图片与目标视频时间点的 Alignment 指令。</small>
>
> > [!card] Full-reference · Ref2VA / Ref2V
> > <span class="ll-badge is-priority">多参考模式</span>
> >
> > **6 个核心字段**
> >
> > 1. `subject_definitions`
> > 2. `summary`
> > 3. `retention_analysis`
> > 4. `detailed_description`
> > 5. `overall_soundscape`
> > 6. `non_diegetic_music`
> >
> > <small class="ll-note">必要时追加 `Do not include`。所有参考标签必须从定义到正文保持同一含义。</small>

## 02 · 核心写法

> [!summary] 提示词公式
> **完整提示词 = 参考素材说明 + 核心创意 + 画面过程说明**

> [!grid-3]
>
> > [!card] 参考素材说明
> > 明确谁 / 什么来自哪张图、哪段视频或哪段音频，以及需要保留什么。
>
> > [!card] 核心创意
> > 用一句话说明这段视频最终要完成什么视觉任务，不在这里堆镜头细节。
>
> > [!card] 画面过程
> > 写清动作如何发生、镜头如何移动、光线和声音如何变化，以及参考素材在什么时间发挥作用。

> [!meta] 不要把“形容词很多”误认为提示词完整
> `cinematic / atmospheric / stunning` 这类词只有在同时说明具体光线、材质、动作、镜头或声音依据时才有意义。H3 更需要的是**可见变化与明确控制关系**。

## 03 · 图生 / 首尾帧

FL2VA 把输入图片当作目标视频关键帧，所以提示词重点写“参考帧之后 / 之前发生什么变化”，不要反复重新描述图片里已经清楚可见的服装、发型和背景。

> [!grid-3]
>
> > [!card] I2V
> > <span class="ll-badge is-source">首帧</span>
> >
> > 单张图片作为视频起始关键帧。
> >
> > **重点**：描述首帧之后发生的动作和镜头变化。
>
> > [!card] L2V
> > <span class="ll-badge is-source">尾帧</span>
> >
> > 单张图片作为视频结束关键帧。
> >
> > **重点**：让前面的过程自然收敛到目标尾帧。
>
> > [!card] FL2V
> > <span class="ll-badge is-source">首帧 + 尾帧</span>
> >
> > 两张图片约束视频两端。
> >
> > **重点**：通常优先连续单镜头，让模型完成插值和状态过渡。

## 04 · Ref2VA 六段式

| 字段 | 负责什么 | 关键要求 |
| --- | --- | --- |
| `subject_definitions` | 定义主体 / 图片 / 视频 / 音频参考 | 每个素材一行；标签后续不改名 |
| `summary` | 一句话概括任务 | 不在这里引入新标签 |
| `retention_analysis` | 记录参考素材出现位置与保留程度 | 明确 fully / partially / transfer / weak 等状态 |
| `detailed_description` | 主要视听过程 | 描述镜头内真正发生的变化 |
| `overall_soundscape` | 环境声、动作声、非语言人声 | 不重复对白 |
| `non_diegetic_music` | 角色听不到的背景音乐 | 写乐器、速度、节奏、动态变化 |

### 参考标签

> [!grid-2]
>
> > [!card] 视觉 / 内容参考
> > - `<Subject N>`：人物、产品、环境、服装、风格、动作等可复用内容
> > - `<Picture N>`：目标帧、关键帧、尾帧或构图锚点
> > - `<Video N>`：整段结构、动作、运镜、剪辑节奏等参考
>
> > [!card] 音频参考
> > - `<Audio N>`：音色、音乐或节奏参考
> > - 有人物声音时，需要与稳定 Speaker ID 对应
> > - 同一标签在所有段落中保持同一含义

### 保留程度

| 视觉参考 | 音频参考 |
| --- | --- |
| `fully_preserved` | `fully_copy` |
| `partially_preserved` | `partially_copy` |
| `attribute_transfer` | `reference` |
| `weak_reference` | `weak_reference` |

### 正文主体顺序

> [!summary] 每个镜头尽量按这个顺序检查
> **构图 → 主体 → 环境 / 光线 → 动作变化 → 运镜 → 声音 → 参考素材出现位置**

## 05 · 镜头与切镜

| 规则 | 怎么理解 |
| --- | --- |
| 一个镜头一种主要运镜 | 不在同一镜头里堆多个互相冲突的运动 |
| 切镜必须带来新信息 | 新主体、新空间、新状态、新视角或新时间 |
| 只是距离 / 角度变化 | 优先 Push / Pull / Pan / Truck / Tilt / Arc / Tracking，而不是切镜 |
| 后续镜头时间戳 | 必须严格递增，且总时长不能超过目标视频时长 |
| FL2VA / L2VA | 通常优先连续单镜头，让插值 / 收敛更自然 |

### 常用运镜

<div class="ll-chip-row">
  <span class="ll-chip">Zoom In / Out</span>
  <span class="ll-chip">Push In / Pull Out</span>
  <span class="ll-chip">Pan Left / Right</span>
  <span class="ll-chip">Truck Left / Right</span>
  <span class="ll-chip">Tilt Up / Down</span>
  <span class="ll-chip">Pedestal Up / Down</span>
  <span class="ll-chip">Arc Shot</span>
  <span class="ll-chip">Tracking Shot</span>
  <span class="ll-chip">Static Shot</span>
  <span class="ll-chip">POV</span>
</div>

需要时再补充幅度与速度：`with small amplitude` / `with large amplitude`、`at slow speed` / `at fast speed`。

## 06 · 对白与声音

> [!grid-2]
>
> > [!card] Speaker / Dialogue
> > 有对白或演唱的主体使用稳定 Speaker ID，例如 `(S1)`、`(S2)`；跨镜头保持一致。
> >
> > 对白正文放进 `<d>...</d>`，保留原语言、原文字和标点，不翻译、不改写。
>
> > [!card] Voiceover / Sound
> > 画外音要明确为 `off-screen voiceover`，并说明画面中人物嘴唇保持闭合，避免误生成口型。
> >
> > `overall_soundscape` 负责环境声、动作声和非语言人声，不重复对白。

## 07 · 常见错误

> [!risk] 高概率错误
> - 对着参考图重复描述已经清楚可见的服装、发型和背景。
> - 一个镜头里同时塞入多种互相冲突的运镜。
> - 6 秒视频却写成 15 秒镜头表。
> - Ref2VA 标签在不同段落中改名，导致引用关系断裂。
> - 只写抽象风格词，不写具体光线、材质、动作和声音依据。
> - 写成故事梗概，却没有描述画面真正如何变化。

## 08 · Agent 原始指令

> [!resource] H3 Agent System Prompt
> [[resources/H3-Agent-System-Prompt|打开完整 Agent 原始指令 →]]
>
> <small class="ll-note">学习和复习优先看本页；只有需要直接复用执行规则、核对固定字段或继续改 Agent 时，再进入原始资源。</small>

## 09 · 待实测

- [ ] 中文 vs 英文 Prompt 的稳定性差异。
- [ ] 短 Prompt vs 结构化长 Prompt 的质量差异。
- [ ] FL2VA 单镜头与多镜头写法差异。
- [ ] Ref2VA 多参考时标签、保留程度对一致性的影响。
- [ ] 不同视频时长下镜头数量的合理范围。

> [!resource] 统一记录测试结果
> [[MiniMax-H3-实测记录|打开 MiniMax H3 实测记录 →]]
