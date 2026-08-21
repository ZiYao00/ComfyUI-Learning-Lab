---
title: MiniMax H3
topic: minimax-h3
type: model-review
status: verified
last_verified: 2026-08-21
cssclasses:
  - learning-page
  - model-guide
---

# MiniMax H3

> [!lead]
> H3 主说明书负责回答：**下载什么、文件放哪里、FL2VA / Ref2VA 怎么选、LoRA 怎么配、运行边界和分辨率怎么设。** 提示词、性能优化和真实测试分别维护在独立附页。

> [!summary] 先记住这两个选择
> **FL2VA**：输入图片本身就是目标视频的关键帧，用于 T2V / I2V / 尾帧 / 首尾帧。
>
> **Ref2VA**：素材用于“参考人物、服装、场景、动作、运镜或声音”，不要求参考图成为目标视频第一帧。

## 01 · 模型下载

**ComfyUI 官方适配仓库：** [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3)

### 核心模型

| 文件（点击下载） | 大小 / 必需 | 作用 |
| --- | --- | --- |
| [minimax_h3_fl2va_pruned_int8_convrot.safetensors](https://huggingface.co/Comfy-Org/MiniMax-H3/resolve/main/diffusion_models/minimax_h3_fl2va_pruned_int8_convrot.safetensors) | 21 GB · FL2VA 必需 | T2V / I2V / 首帧 / 尾帧 / 首尾帧 |
| [minimax_h3_ref2va_pruned_int8_convrot.safetensors](https://huggingface.co/Comfy-Org/MiniMax-H3/resolve/main/diffusion_models/minimax_h3_ref2va_pruned_int8_convrot.safetensors) | 21 GB · Ref2VA 必需 | 多参考图片 / 视频 / 音频生成 |
| [qwen3vl_32b_minimax_h3_nvfp4_awq.safetensors](https://huggingface.co/Comfy-Org/MiniMax-H3/resolve/main/text_encoders/qwen3vl_32b_minimax_h3_nvfp4_awq.safetensors) | 15.7 GB · 必需 | 理解 Prompt、图片和参考素材 |
| [minimax_h3_video_vae_fp16.safetensors](https://huggingface.co/Comfy-Org/MiniMax-H3/resolve/main/vae/minimax_h3_video_vae_fp16.safetensors) | 5.21 GB · 必需 | 视频 latent 编码 / 解码 |
| [minimax_h3_audio_vae_fp32.safetensors](https://huggingface.co/Comfy-Org/MiniMax-H3/resolve/main/vae/minimax_h3_audio_vae_fp32.safetensors) | 605 MB · 必需 | 音频 latent 编码 / 解码 |

**两套都装：** 5 个核心文件约 **63.5 GB**。

**只跑 FL2VA：** 不下载 Ref2VA 主模型即可。

**只跑 Ref2VA：** 不下载 FL2VA 主模型即可。

### Turbo LoRA（可选）

| 文件（点击下载） | 用途 | 放置目录 |
| --- | --- | --- |
| [minimax_h3_fl2v_turbo_8step_v1.0_comfyui_bf16.safetensors](https://huggingface.co/lightx2v/Minimax-h3-Turbo/resolve/main/minimax_h3_fl2v_turbo_8step_v1.0_comfyui_bf16.safetensors) | FL2VA · 8-step Turbo | `models/loras/` |
| [minimax_h3_ref2v_turbo_4step_v0.1_comfyui_bf16.safetensors](https://huggingface.co/Comfy-Org/MiniMax-H3/resolve/main/loras/minimax_h3_ref2v_turbo_4step_v0.1_comfyui_bf16.safetensors) | Ref2VA · 4-step Turbo | `models/loras/` |

> 当前 ComfyUI 官方模板的 model scan 会检查对应 Turbo LoRA。Turbo 用于减少采样步数；不是 H3 主模型。

---

## 02 · 文件放置位置

```text
ComfyUI/
└── models/
    ├── diffusion_models/
    │   ├── minimax_h3_fl2va_pruned_int8_convrot.safetensors
    │   └── minimax_h3_ref2va_pruned_int8_convrot.safetensors
    │
    ├── text_encoders/
    │   └── qwen3vl_32b_minimax_h3_nvfp4_awq.safetensors
    │
    ├── vae/
    │   ├── minimax_h3_video_vae_fp16.safetensors
    │   └── minimax_h3_audio_vae_fp32.safetensors
    │
    └── loras/
        ├── minimax_h3_fl2v_turbo_8step_v1.0_comfyui_bf16.safetensors
        └── minimax_h3_ref2v_turbo_4step_v0.1_comfyui_bf16.safetensors
```

---

## 03 · 这 5 个核心文件分别干什么

```text
Prompt / 图片 / 视频 / 音频
→ Qwen3-VL 理解条件
→ FL2VA 或 Ref2VA 生成 Video + Audio latent
→ Video VAE / Audio VAE 解码
→ 视频 + 立体声音频
```

### FL2VA

普通生成路线：

- T2V：文生视频。
- I2V：首帧图生视频。
- L2V：尾帧控制。
- FL2V：首帧 + 尾帧控制。

**记忆：图片本身就是目标视频的关键帧 → FL2VA。**

### Ref2VA

多参考生成路线，可使用：

- 人物参考图。
- 服装 / 场景 / 风格参考图。
- 动作 / 运镜参考视频。
- 声音参考。

**记忆：素材只是告诉模型“要参考什么”，不一定成为视频第一帧 → Ref2VA。**

### Qwen3-VL

负责理解：

- Prompt。
- 图片内容。
- 多参考素材之间的关系。

它是条件编码器，不是视频生成主模型。

### Video VAE

负责视频画面与 video latent 之间的编解码。

### Audio VAE

负责声音与 audio latent 之间的编解码。

H3 的视频和音频是联合生成的，不是视频生成完以后再单独配音。

---

## 04 · FL2VA / Ref2VA 怎么选

| 需求 | 使用 |
| --- | --- |
| 只有 Prompt | **FL2VA** |
| 一张图就是视频第一帧 | **FL2VA** |
| 首帧 + 尾帧控制 | **FL2VA** |
| 多张人物图锁定人物 | **Ref2VA** |
| 人物 + 服装 + 场景多参考 | **Ref2VA** |
| 参考视频动作 / 运镜 | **Ref2VA** |
| 参考人物声音 | **Ref2VA** |

### 名称速记

`Ref2VA` = Reference → Video + Audio

- `V` = Video
- `A` = Audio

社区常见的：

- Ref2V
- Ref2Vid
- R2V

一般都在描述 Reference-to-Video 这条路线；H3 官方主模型名称是 `Ref2VA`。

---

## 05 · LoRA 怎么选

**LoRA 跟主模型走。**

| 当前主模型 | LoRA 优先选择 |
| --- | --- |
| `minimax_h3_fl2va...` | FL2VA / FL2V 版本 |
| `minimax_h3_ref2va...` | Ref2VA / Ref2V / Ref2Vid / R2V 版本 |

Civitai 同一个 LoRA 如果同时提供 FL2VA 与 Ref2VA 两版：

1. 看当前工作流加载哪个主模型。
2. 下载对应版本。
3. 不默认跨主模型混用。

---

## 06 · 运行边界

### 帧数

- H3 帧数规则：`17n + 5`。
- 与 Wan 常见的 `8n + 1` 不同，不要混用。

### 时长

- 当前教程建议生成时长：**4 ~ 15 秒**。
- 若从秒数换算帧数，可使用：

```text
max(5, round(a * 24)) + (5 - (max(5, round(a * 24)) % 17)) % 17
```

其中 `a` 为目标秒数。

### 四类输入

| 输入 | FL2VA | Ref2VA | 备注 |
| --- | --- | --- | --- |
| 文本 | 支持 | 支持 | 支持多语言；教程记录英文稳定性略好；Prompt 最长约 7000 字符 |
| 图片 | 1 张作首帧或尾帧；2 张作首尾帧 | 最多 9 张参考图 | FL2VA 把图片当关键帧；Ref2VA 主要参考人物、风格、构图等内容 |
| 视频 | 不支持 | 最多 3 段 | 单段 2 ~ 15 秒，总时长不超过 15 秒；用于动作、运镜、音色等参考 |
| 音频 | 不支持 | 最多 3 段 | 单段 2 ~ 15 秒，总时长不超过 15 秒；不能只给纯音频，需搭配图片或视频 |

> 以上输入上限与时长规则来自 2026-08-21 教程笔记，后续以实际工作流和官方更新继续复核。

---

## 07 · 分辨率

### 基本规则

- ComfyUI `Resolution Selector`：`multiple = 32`。
- H3 当前画布上限按 `768 × 1344` 的总像素面积控制。
- 16:9 官方 768p 档：`0.98 → 1344 × 768`。
- 9:16 对应：`0.98 → 768 × 1344`。
- 不要使用 `1.0 → 1376 × 768`，会超过当前 H3 上限。

### 16:9 / 9:16 完整对照

| MP | 16:9 | 9:16 |
| ---: | --- | --- |
| 0.2 | `608 × 352` | `352 × 608` |
| 0.3 | `736 × 416` | `416 × 736` |
| 0.4 | `864 × 480` | `480 × 864` |
| 0.5 | `960 × 544` | `544 × 960` |
| 0.6 | `1056 × 608` | `608 × 1056` |
| 0.7 | `1152 × 640` | `640 × 1152` |
| 0.8 | `1216 × 672` | `672 × 1216` |
| 0.9 | `1280 × 736` | `736 × 1280` |
| **0.98** | **`1344 × 768`** | **`768 × 1344`** |

**4090 使用建议：**先用 `0.6 ~ 0.8` 调 Prompt / 动作，确定后再用 `0.9 ~ 0.98` 出片。

### 其它常见比例速查

以下尺寸按 ComfyUI `Resolution Selector`、`multiple=32` 计算：

| 比例 | 0.5 MP | 0.8 MP | 接近 H3 上限 |
| --- | --- | --- | --- |
| 1:1 | `736 × 736` | `928 × 928` | `992 × 992`（0.96） |
| 2:3 竖图 | `576 × 896` | `736 × 1120` | `832 × 1216`（0.96） |
| 3:2 横图 | `896 × 576` | `1120 × 736` | `1216 × 832`（0.96） |
| **3:4 竖图** | `640 × 832` | **`800 × 1056`** | **`864 × 1184`**（0.98） |
| 4:3 横图 | `832 × 640` | `1056 × 800` | `1184 × 864`（0.98） |
| **9:16 竖屏** | `544 × 960` | **`672 × 1216`** | **`768 × 1344`**（0.98） |
| 16:9 横屏 | `960 × 544` | **`1216 × 672`** | **`1344 × 768`**（0.98） |
| 21:9 超宽 | `1120 × 480` | `1408 × 608` | `1536 × 672`（0.98） |

### 手动输入尺寸时

如果不用 `Resolution Selector`、而是手工填宽高，可以优先选择更标准的比例：

- 3:4：`768 × 1024`、`864 × 1152`。
- 9:16：`672 × 1184`、`736 × 1312`。

这两组属于手动尺寸建议；和 `Resolution Selector` 自动计算出来的尺寸不要混为一套。

> 显存占用还受视频时长、Ref2VA 参考数量、offload、LoRA 等影响。4090 的实际舒适区后续以 RH 实测记录为准。

---

## 08 · 官方工作流

- [T2V 工作流](https://github.com/Comfy-Org/workflow_templates/blob/main/templates/video_minimax_h3_t2v.json)
- [I2V 工作流](https://github.com/Comfy-Org/workflow_templates/blob/main/templates/video_minimax_h3_i2v.json)
- [R2V 工作流](https://github.com/Comfy-Org/workflow_templates/blob/main/templates/video_minimax_h3_r2v.json)
- [ComfyUI MiniMax H3 官方教程](https://docs.comfy.org/tutorials/video/minimax/minimax-h3)
- [MiniMax H3 官方仓库](https://huggingface.co/MiniMaxAI/MiniMax-H3)

---

## 09 · 深入学习

- [[MiniMax-H3-提示词|提示词]] — Base / Ref2VA 的提示词结构、镜头、声音、参考素材写法。
- [[MiniMax-H3-加速与优化|加速与优化]] — Attention、Turbo LoRA、Cache、混合模型等方案。
- [[MiniMax-H3-实测记录|实测记录]] — RH / RTX 4090 的参数、显存、生成时间、失败案例。
- [[resources/H3-Agent-System-Prompt|H3 Agent System Prompt]] — 教程提供的完整 Agent 执行指令，作为原始资源保存。

---

## 10 · 30 秒复习

```text
核心 5 文件：
FL2VA + Ref2VA + Qwen3-VL + Video VAE + Audio VAE

FL2VA：
文生 / 首帧 / 尾帧 / 首尾帧

Ref2VA：
多参考图片 / 视频 / 音频

LoRA：
FL2VA 主模型 → FL2V / FL2VA LoRA
Ref2VA 主模型 → Ref2V / Ref2VA / Ref2Vid LoRA

9:16（Resolution Selector）：0.8 → 672×1216 / 0.98 → 768×1344
3:4（Resolution Selector）：0.8 → 800×1056 / 0.98 → 864×1184
手动尺寸：9:16 可用 672×1184；3:4 可用 768×1024
```
