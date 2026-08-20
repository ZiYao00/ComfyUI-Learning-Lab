# ComfyUI Learning Lab

一个以 **学习、理解、实践、复习、讲解** 为目标的 ComfyUI 学习项目。

本项目不是 ComfyUI 百科，也不尝试镜像官方文档、模型站或插件注册表。它只整理真正经过学习与筛选、值得长期掌握的知识点，并把这些知识组织成可以复习、可以教学、可以验证的学习模块。

## 当前阶段

项目从 **MiniMax H3** 开始，以它作为第一个完整样板，验证以下方法是否成立：

1. 一个新模型如何从“看不懂”整理成“能解释”。
2. 模型文件、模式、LoRA、分辨率等容易混淆的概念如何形成稳定记忆。
3. Obsidian 笔记如何同时服务于自学、复习和讲解。
4. 学习内容如何保留来源与验证日期，避免快速变化的 ComfyUI 生态造成知识过期。
5. 未来如何在不重复维护内容的前提下发布为网站。

## 仓库结构

```text
ComfyUI-Learning-Lab/
├── README.md
├── docs/
│   ├── PROJECT.md
│   ├── ROADMAP.md
│   └── TASKS.md
└── vault/
    ├── .obsidian/
    ├── 00-导航.md
    ├── _legacy/        # 旧资料待整理区
    ├── 知识星球.backup/ # 本地备份，Git 忽略
    └── Models/
        └── MiniMax-H3/
```

- `docs/`：项目目标、路线和任务跟进，不存具体 ComfyUI 学习正文。
- `vault/`：Obsidian Vault，也是正式学习内容的唯一知识源。
- `vault/_legacy/`：旧笔记待整理区；内容尚未按当前规范验证。
- `vault/知识星球.backup/`：外部备份资料，仅本地保留，Git 忽略。
- HTML / 网站未来从 Markdown 构建生成，不与 Markdown 维护两套正文。

## 核心原则

- **Single Source of Truth**：学习正文只维护 Markdown 一份。
- **Learning first**：优先回答“为什么、什么时候用、和什么容易混淆”。
- **Evidence first**：快速变化的信息尽量保留官方来源与最后核对日期。
- **Practice before scale**：先把 MiniMax H3 做好，再决定整个 ComfyUI 学习体系的结构。
- **No premature taxonomy**：不为了“看起来完整”提前创建大量空目录与空文档。
- **No model binaries**：仓库不保存大型模型权重、第三方 LoRA 二进制文件。

## 开始阅读

使用 Obsidian 打开 `vault/` 目录，然后从：

- `00-导航.md`
- `Models/MiniMax-H3/MiniMax-H3.md`

开始。

项目路线见 [docs/ROADMAP.md](docs/ROADMAP.md)，当前执行任务见 [docs/TASKS.md](docs/TASKS.md)。
