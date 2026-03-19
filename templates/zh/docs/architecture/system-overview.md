# System Overview

从主要组件及其交互方式来描述系统。

## 建议章节
- entry points
- core domains or services
- data stores and external dependencies
- major request or event flows
- important background jobs, queues, or scheduled work
- main operational signals such as logs, metrics, and traces

## 这份文档应回答的问题
- 系统的主要部分有哪些？
- 业务逻辑应该放在哪里？
- 哪些依赖是外部的，哪些是内部的？
- 哪些部分可以安全地一起修改？
- 变更后最重要、最需要验证的是哪些流程？

## 编写指引
- 从系统稳定的整体形态开始，而不是从低层实现细节开始。
- 优先使用简短图示、表格或要点，而不是密集长文。
- 当更深层细节位于 domain、layering 或 decision 文档中时，链接出去。

## 维护规则
当系统形态或主要职责变化时，更新此文件。
