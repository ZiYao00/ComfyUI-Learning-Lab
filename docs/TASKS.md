# ComfyUI Learning Lab Tasks

> 当前任务跟进清单。完成后直接勾选；Roadmap 负责阶段方向，本文件负责执行状态。

## Phase 0 - 项目基础

- [x] 确定项目名 `ComfyUI-Learning-Lab`。
- [x] 建立 `README.md`、`docs/`、`vault/`。
- [x] 建立 Obsidian 导航页 `vault/00-导航.md`。
- [x] 将 MiniMax H3 收口为单文件主说明书。
- [x] 初始化独立 Git 仓库，默认分支 `main`。
- [x] 建立 `.gitignore`。
- [x] 忽略 `vault/知识星球.backup/`。
- [x] 将旧 `comfyui.backup` 初步整理到 `vault/_legacy/`。
- [x] 建立旧资料迁移规则。
- [ ] 设计并确认 `.obsidian` 哪些设置进入 Git、哪些保持本地。
- [ ] 完成首次人工确认后的 Git commit。

## Phase 1 - MiniMax H3 实际验证

- [x] 完成 `Models/MiniMax-H3/MiniMax-H3.md` 基础说明书。
- [ ] 在 RH / RTX 4090 跑一次 FL2VA I2V。
- [ ] 记录 FL2VA 的模型、steps、分辨率、时长、显存、生成时间。
- [ ] 在 RH / RTX 4090 跑一次 Ref2VA 多参考。
- [ ] 记录 Ref2VA 的参考数量、`ref_image_size`、steps、分辨率、时长、显存、生成时间。
- [ ] 对比 Turbo / 非 Turbo 的速度与质量。
- [ ] 收集至少 3 个真实失败案例与修复方式。
- [ ] 根据实测结果修订 H3 说明书。
- [ ] 判断 H3 是否需要独立的“实战 / 故障排查”附页。

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
- [ ] 评估 Quartz / 其它 Markdown 静态发布方案。
- [ ] 保证网站继续以 `vault/` Markdown 为唯一内容源。
- [ ] 验证导航、搜索、移动端阅读。
- [ ] 决定公开内容与个人私有笔记的边界。
