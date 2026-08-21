# ComfyUI Learning Lab · 文档设计系统

> 当前版本：v0.2 · 2026-08-21  
> 状态：**H3 四篇正式学习页已完成迁移并通过当前人工阅读验收，可作为后续页面的视觉基线。**  
> 第一张视觉样板页：`vault/Models/MiniMax-H3/MiniMax-H3-加速与优化.md`

## 安装到自己的 Obsidian

仓库内提供两份 CSS Snippet：

```text
vault/.obsidian/snippets/
├── h3-compact.css
└── learning-lab.css
```

如果你不是直接把本项目的 `vault/` 当作 Obsidian Vault，而是把笔记复制到自己现有的 Obsidian 知识库，需要把这两个 CSS 文件一并复制到**你自己的 Vault**：

```text
你的 Obsidian Vault/
└── .obsidian/
    └── snippets/
        ├── h3-compact.css
        └── learning-lab.css
```

`.obsidian` 通常是隐藏目录；如果 `snippets/` 不存在，可以手动创建。

复制完成后：

1. 打开 **Obsidian → 设置 → 外观 → CSS 代码片段**。
2. 点击刷新 / 重新载入代码片段。
3. 启用 `learning-lab`。
4. 仍在使用旧 H3 紧凑页面时，同时启用 `h3-compact`。

如果文件没有放进当前 Vault 的 `.obsidian/snippets/`，Obsidian 的“CSS 代码片段”设置里就不会出现它们。

### 两个 CSS 的职责

| 文件 | 用途 | 当前建议 |
| --- | --- | --- |
| `learning-lab.css` | Learning Lab Design System：标题、Card、Grid、Badge、表格、说明块、响应式布局 | **主样式，建议启用** |
| `h3-compact.css` | 早期 H3 紧凑说明书样式，保留兼容旧页面 | 暂时一并复制；旧页面需要时启用 |

CSS 只负责视觉表现，不保存知识正文；即使没有启用，Markdown / Wikilink / Callout 仍然保留基本可读性。

## 目标

Learning Lab 的 Markdown 不只要“能读”，还要支持**快速扫描、横向比较、回看定位和长期维护**。

设计系统遵循四条原则：

1. **语义和样式分离**：Markdown 负责内容与关系，CSS 负责视觉表现。
2. **相关信息靠近**：需要比较的对象优先并排，不强迫读者依赖上下文记忆。
3. **信息密度有层级**：结论、事实、状态、风险、来源、资源使用不同视觉权重。
4. **渐进兼容**：关闭 CSS 时仍能按普通 Markdown / Callout 阅读；未来可映射到 Quartz / Starlight。

## 页面层级

| 层级 | 用途 | 规则 |
| --- | --- | --- |
| H1 | 页面身份 | 一页只出现一次；标题本身不承担说明正文 |
| Lead | 页面范围 / 读法 | 1 段，告诉读者本页解决什么问题 |
| Summary | 当前结论 | 优先放选择结论、默认策略、关键判断 |
| H2 | 大分类 | 使用 `01 ·`、`02 ·` 等稳定编号，便于长页定位 |
| H3 | 局部主题 | 只在单个大分类内部确有层级时使用 |
| 正文 | 解释 | 避免连续多段无视觉锚点的长墙文字 |
| Meta / 小字 | 来源、状态、限定条件 | 降低视觉权重，不与结论抢层级 |

## 组件选择

### Card / Grid

**适合：** 2~3 个需要直接比较的方案、模式或概念。

- 两项：`[!grid-2]` — 正常宽度固定两列；极窄阅读区再退回单列。
- 三项：`[!grid-3]` — 正常宽度固定三列，不允许出现尴尬的“2 + 1”孤儿布局；极窄阅读区直接退回单列。
- 数量不固定：`[!grid-auto]` — 由可用宽度自动换行。
- 子项使用 `[!card]`

`grid-2 / grid-3` 使用 CSS Container Query，以**当前笔记正文宽度**而不是整个屏幕宽度判断响应式布局，因此在 Obsidian 左右分栏时也能正确工作。

不要为了“好看”把所有内容卡片化。卡片主要解决**并列关系和空间比较**。

### Table

**适合：** 4 个以上对象，或多个对象需要按固定字段比较。

典型字段：兼容性、路线、状态、用途、优先级、实测参数。

表格中的每一列都应该承担比较意义；如果只是把段落强行切成单元格，则不使用表格。

### Summary

`[!summary]` 只放当前最重要的选择结论或默认策略。

同一屏幕不宜连续出现多个 Summary，否则视觉优先级失效。

### Meta

`[!meta]` 用于：

- 为什么这样安排；
- 来源限制；
- 验证方法；
- 需要知道、但不应抢主结论的信息。

### Risk

`[!risk]` 用于风险、冲突、兼容性问题或当前明确不推荐的路线。

### Resource

`[!resource]` 用于：

- 内部深入阅读；
- 下载入口；
- GitHub / Hugging Face 等外部资源；
- 跨页面的数据或实测入口。

避免在正文中直接摆裸 URL。

### Badge

Badge 只表达短状态，不承载正文：

- `当前优先`
- `教程记录`
- `官方`
- `社区方案`
- `待实测`
- `已验证`

当前实现使用少量 inline HTML：

```html
<span class="ll-badge is-source">教程记录</span>
<span class="ll-badge is-test">待实测</span>
<span class="ll-badge is-priority">当前优先</span>
```

### Chip

只有名称、几乎没有独立说明价值的一组对象，用 Chip 压缩纵向长度，不为每个名称单独创建 H3。

```html
<div class="ll-chip-row">
  <span class="ll-chip">EasyCache</span>
  <span class="ll-chip">TeaCache</span>
  <span class="ll-chip">Spectrum</span>
</div>
```

## 内容整理规则

### 先判断关系，再决定版式

源资料里出现 4 个名称，不代表需要 4 个同级标题。

整理前先判断它们是：

- 并列方案；
- 上游 / 下游关系；
- 同一路线的不同兼容实现；
- 主方案 / 实验方案；
- 可组合方案；
- 互斥方案。

只有关系明确后，才决定使用 Card、Table、流程或普通正文。

### 结论与证据分开

例如：

- `教程记录：约 1.3×+` 是来源事实；
- `当前优先测试 SageAttention` 是项目策略；
- `RTX 4090 实测为 1.28×` 才是项目验证结果。

三者不能写成同一种视觉层级。

### 知识页与实测页分工

知识页保留：

- 有哪些方案；
- 怎么选；
- 方案关系；
- 当前策略。

实测页保留：

- 环境；
- 参数；
- 显存；
- 时间；
- 画质；
- 失败案例；
- 最终验证结果。

不要在两个页面重复维护同一份 Checklist 或测试数据。

## HTML 使用边界

正文主体继续使用 Markdown / Wikilink / Callout。

允许少量 HTML 作为**无业务语义的视觉原语**：

- Badge；
- Chip；
- 必要的布局容器。

不建议使用 HTML 重写：

- 标题；
- 表格；
- 正文段落；
- 链接体系；
- 大块业务内容。

这样可以减少未来 Quartz / Starlight 的迁移成本。

## CSS

项目级样式：

`vault/.obsidian/snippets/learning-lab.css`

只有 frontmatter 包含以下 class 的页面才会应用：

```yaml
cssclasses:
  - learning-page
```

CSS 使用 Obsidian 自身的主题变量，不固定浅色 / 深色具体颜色。`grid-2 / grid-3` 使用固定列数 + Container Query：正常正文宽度下保持完整两列 / 三列，真正窄到不适合横排时直接退回单列；`grid-auto` 才使用 `auto-fit + minmax()` 自动换行。

当前没有创建或覆盖 `appearance.json`。Snippet 是否启用保持为用户本机设置，不纳入本轮项目配置。

## 未来 Quartz / Starlight

Markdown 语义保持不变。

- **Quartz**：优先映射现有 Obsidian Callout，并在站点 `custom.scss` 复刻 Design Tokens / Grid / Card。
- **Starlight**：构建层把相同语义映射成 Card、Tabs、Steps 或自定义 Astro Components。

不为了未来网站提前把 Vault 正文改成 Quartz / Starlight 专用语法。

## 当前验收范围

v0.2 已应用到 H3 的四篇正式学习页：

- `MiniMax-H3.md` — 主说明书 / 速查型页面。
- `MiniMax-H3-提示词.md` — 结构 / 比较型页面。
- `MiniMax-H3-加速与优化.md` — 方案 / 决策型页面。
- `MiniMax-H3-实测记录.md` — 数据 / 任务型页面。

当前继续观察：

- 大标题 / H2 / 正文层级是否舒服；
- `grid-2 / grid-3` 在主窗口与窄分栏下是否保持合理关系；
- Light / Dark 是否都能阅读；
- Badge / Chip / Table 是否过度设计；
- 卡片数量是否真正帮助比较，而不是为了视觉效果滥用；
- 页面是否比原版更容易快速定位和回看。

`resources/` 中的原始 Agent 指令暂不套学习页卡片结构，优先保持源文本完整、便于复制和核对。后续新模型直接复用同一 Design System，但仍需根据内容关系选择组件。
