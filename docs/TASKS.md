# ComfyUI Learning Lab Tasks

> 当前任务跟进清单。完成后直接勾选；Roadmap 负责阶段方向，本文件负责执行状态。

## Phase 0 - 项目基础

- [x] 确定项目名 `ComfyUI-Learning-Lab`。
- [x] 建立 `README.md`、`docs/`、`vault/`。
- [x] 建立 Obsidian 导航页 `vault/00-导航.md`。
- [x] 完成 H3 单文件主说明书的第一阶段样板（后续已升级为主说明书 + 按需附页）。
- [x] 初始化独立 Git 仓库，默认分支 `main`，并建立远端跟踪。
- [x] 建立 `.gitignore`。
- [x] 忽略 `vault/知识星球.backup/`。
- [x] 将旧 `comfyui.backup` 初步整理到 `vault/_legacy/`。
- [x] 建立旧资料迁移规则。
- [x] 明确 `.obsidian` 当前版本控制边界：项目级 CSS Snippet 跟随仓库；workspace / cache 等机器状态保持本地。

## Phase 1 - MiniMax H3 实际验证

- [x] 完成 `Models/MiniMax-H3/MiniMax-H3.md` 基础说明书。
- [x] 将 H3 从单文件样板升级为“主说明书 + 按需附页”结构。
- [x] 建立 H3 提示词附页。
- [x] 建立 H3 加速与优化附页。
- [x] 建立 H3 实测记录附页。
- [x] 保存 H3 Agent 系统指令到 `resources/`，与学习正文分离。
- [x] 建立 `docs/DESIGN-SYSTEM.md` 与项目级 Obsidian CSS Snippet。
- [x] 将 `MiniMax-H3-加速与优化.md` 重做为第一张视觉样板页。
- [x] 修正 `grid-3` 的 2+1 换行问题：正常宽度固定三列，极窄正文区直接退回单列。
- [x] 将 Design System 应用到 H3 主说明书 / 提示词 / 实测记录。
- [x] 在 README / Design System 中补充 `h3-compact.css`、`learning-lab.css` 的复制与启用教程。
- [x] 当前 H3 正式学习页版式已通过人工阅读验收，作为 Design System v0.2 基线。
- [ ] 后续在浅色 / 深色、不同主题和极窄分栏下继续做回归观察；发现问题再修，不阻塞当前提交。
- [ ] 在 RH / RTX 4090 跑一次 FL2VA I2V。
- [ ] 记录 FL2VA 的模型、steps、分辨率、时长、显存、生成时间。
- [ ] 在 RH / RTX 4090 跑一次 Ref2VA 多参考。
- [ ] 记录 Ref2VA 的参考数量、`ref_image_size`、steps、分辨率、时长、显存、生成时间。
- [ ] 对比 Turbo / 非 Turbo 的速度与质量。
- [ ] 收集至少 3 个真实失败案例与修复方式。
- [ ] 根据实测结果修订 H3 说明书及对应附页。
- [ ] 根据失败案例数量判断是否再拆独立“故障排查”页。

## Phase 2 - 旧资料逐步迁移

> 不按旧目录顺序清空；按当前实际学习需要逐项迁移。

### Foundations

- [ ] 复核“安装与报错”旧笔记，提炼高复用内容。
- [ ] 复核“尺寸比例”旧笔记，与当前 Resolution Selector 规则统一。

### Models / Video

- [ ] 从 `_legacy/Video` 选择一个实际会用的第二模型作为新样板。
- [ ] 复核 Wan 相关旧笔记。
- [ ] 复核 Hunyuan 相关旧笔记。
- [ ] 复核 LTX 相关旧笔记。

### Plugins

- [ ] 先从常用插件中挑 1 个做“插件学习页”样板。
- [ ] 评估插件内容是否适合单文件说明书结构。

### Prompts / Training / Resources

- [ ] 复核提示词基础内容，删除纯收藏和过期规则。
- [ ] 复核 LoRA 训练旧笔记。
- [ ] 复核资源入口，保留仍有效且高频使用的链接。

## Phase 3 - 第二个模型样板

- [ ] 选择与 H3 结构差异明显、且当前会实际使用的模型。
- [ ] 按当前“说明书式”结构完成第一版。
- [ ] 实际运行验证。
- [ ] 与 H3 对比哪些章节真正通用。
- [ ] 记录当前结构不适用的地方。

## Phase 4 - Model Learning Template v1

- [ ] 至少完成 2 个真实模型样板后再开始。
- [ ] 定义主说明书的信息优先级。
- [ ] 定义必须保留的来源 / `last_verified` 信息。
- [ ] 定义模型下载、安装路径、模式判断、参数、实战记录格式。
- [ ] 定义“什么时候拆附页”的规则。
- [ ] 建立正式模板文件。

## Phase 5 - 学习体系扩展

- [ ] 根据真实内容增长决定是否建立正式 `Plugins/`。
- [ ] 根据真实内容增长决定是否建立正式 `Workflows/`。
- [ ] 根据真实内容增长决定是否建立正式 `Foundations/`。
- [ ] 优化 `00-导航.md`，按已存在的正式学习模块扩展导航。

## Phase 6 - 网站原型

- [ ] 至少有 3 个稳定学习模块后再启动。
- [x] 暂定网站技术候选：Quartz + Starlight。
- [ ] 使用同一批 `vault/` Markdown 制作 Quartz 小规模原型。
- [ ] 使用同一批 `vault/` Markdown 制作 Starlight 小规模原型。
- [ ] 对比 Obsidian Wikilink / 双链、导航、搜索、移动端阅读和界面定制成本。
- [ ] 决定最终单用 Quartz、单用 Starlight，还是保留两种构建路线。
- [ ] 保证网站继续以 `vault/` Markdown 为唯一内容源。
- [ ] 决定公开内容与个人私有笔记的边界。
