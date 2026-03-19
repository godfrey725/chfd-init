# 文档索引

将此文件作为仓库指引的主导航入口。

## 推荐阅读顺序
1. 仓库根目录的 `../AGENTS.md`
2. `standards/README.md`
3. 当系统结构或归属相关时，阅读 `architecture/README.md`
4. 对进行中的工作，阅读 `plans/active/README.md`
5. 在最终验证前，阅读 `runbooks/verification.md`

## 如何使用这棵文档树
- 当需要决定如何工作时，从 standards 开始。
- 在修改边界、依赖关系或归属前，先阅读 architecture 文档。
- 对需要可持续执行上下文的非简单工作，使用 plans。
- 对不应只存在于计划中的稳定工程或架构选择，使用 decisions。
- 对本地开发、调试、可观测性和验证流程，使用 runbooks。

## 分区
### Standards
- `standards/` —— 编码、测试、日志、审查和仓库行为的稳定规则
- 从 `standards/README.md` 开始

### Architecture
- `architecture/` —— 系统形态、依赖方向和领域边界
- 从 `architecture/README.md` 开始

### Plans
- `plans/active/` —— 正在执行中的计划
- `plans/completed/` —— 已完成工作，保留作历史与追踪记录
- `plans/tech-debt/` —— 已知重要债务，但尚未排期

### Decisions
- `decisions/README.md` —— 使用 ADR 风格记录可长期保留的技术决策

### Runbooks
- `runbooks/local-dev.md` —— 本地环境搭建和日常开发流程
- `runbooks/debugging.md` —— 安全且高效的问题排查路径
- `runbooks/observability.md` —— 日志、指标、追踪与生产信号的使用方法
- `runbooks/verification.md` —— 完成前必须执行的验证

## 何时更新文档
在以下情况更新此文档树：
- 仓库规则发生变化
- 架构或归属边界发生变化
- 验证工作流发生变化
- 某种重复提示模式应沉淀为文档指引
- 某个稳定决策不应只保留在计划或评审讨论中

## 扩展指引
- 保持文档简短、明确、便于代理执行。
- 优先写操作性指引，而不是叙事性背景。
- 将稳定规则放在 `standards/`。
- 将任务专属的执行细节放在 `plans/`。
- 将长期有效的权衡与选择放在 `decisions/`。
- 将可重复执行的流程放在 `runbooks/`。
- 新增项目级指引时，从这里加链接，保证可发现性。
