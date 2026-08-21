# ComfyUI Learning Lab

一个以 **学习、理解、实践、复习、讲解** 为目标的 ComfyUI 学习项目。

本项目不是 ComfyUI 百科，也不尝试镜像官方文档、模型站或插件注册表。它只整理真正经过学习与筛选、值得长期掌握的知识点，并把这些知识组织成可以复习、可以教学、可以验证的学习模块。

## 当前阶段

项目从 **MiniMax H3** 开始，并已完成第一轮结构与版式样板验证。目前 H3 不再是单文件笔记，而是：

```text
MiniMax-H3/
├── MiniMax-H3.md                # 主说明书 / 速查入口
├── MiniMax-H3-提示词.md         # 结构 / 比较型学习页
├── MiniMax-H3-加速与优化.md     # 方案 / 决策型学习页
├── MiniMax-H3-实测记录.md       # 数据 / 任务型记录页
└── resources/
    └── H3-Agent-System-Prompt.md # 原始可复用资源
```

这一阶段已经验证：

1. 一个模型应优先维护 **1 篇主说明书 + 若干按需附页**，而不是不断追加“第 2 篇 / 第 3 篇”。
2. 模型文件、模式、LoRA、分辨率等容易混淆的概念，可以通过表格、Card、双栏 / 三栏和状态组件降低回看成本。
3. Obsidian 笔记需要同时服务于自学、复习和讲解，内容结构与视觉层级应分开设计。
4. 学习内容需要区分官方 / 教程 / 社区 / 待实测 / 已验证，避免快速变化的 ComfyUI 生态造成知识失真。
5. Markdown 继续作为唯一正文源；未来网站暂定评估 **Quartz + Starlight**，不维护第二套 HTML 正文。

当前下一阶段重点是 **RH / RTX 4090 的真实工作流验证**，而不是继续无边界扩充 H3 理论内容。

## 仓库结构

```text
ComfyUI-Learning-Lab/
├── README.md
├── docs/
│   ├── PROJECT.md
│   ├── ROADMAP.md
│   ├── TASKS.md
│   └── DESIGN-SYSTEM.md
└── vault/
    ├── .obsidian/
    │   └── snippets/
    │       ├── h3-compact.css
    │       └── learning-lab.css
    ├── 00-导航.md
    ├── _legacy/         # 旧资料待整理区
    ├── 知识星球.backup/ # 本地备份，Git 忽略
    └── Models/
        └── MiniMax-H3/
            ├── MiniMax-H3.md
            ├── MiniMax-H3-提示词.md
            ├── MiniMax-H3-加速与优化.md
            ├── MiniMax-H3-实测记录.md
            └── resources/
                └── H3-Agent-System-Prompt.md
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

### 启用项目版式

如果直接把仓库里的 `vault/` 作为 Obsidian Vault，项目 CSS 位于：

```text
vault/.obsidian/snippets/
├── h3-compact.css
└── learning-lab.css
```

如果把这些笔记放进你自己的 Obsidian Vault，请把上面两个 CSS 文件复制到：

```text
你的 Vault/.obsidian/snippets/
```

然后进入 **设置 → 外观 → CSS 代码片段**，刷新列表并启用 `learning-lab`；仍使用旧 H3 紧凑页面时可同时启用 `h3-compact`。

完整的版式组件、安装说明与使用规范见 [docs/DESIGN-SYSTEM.md](docs/DESIGN-SYSTEM.md)。

项目路线见 [docs/ROADMAP.md](docs/ROADMAP.md)，当前执行任务见 [docs/TASKS.md](docs/TASKS.md)。
