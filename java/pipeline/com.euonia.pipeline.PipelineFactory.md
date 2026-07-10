# PipelineFactory

> PipelineFactory 负责创建 Pipeline 的实例。它抽象了创建逻辑，允许使用不同的 Pipeline 实现，而无需更改依赖它的客户端代码。

- **Type**: interface
- **Package**: `com.euonia.pipeline`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### create

> 创建一个新的 Pipeline 实例，并指定上下文和响应类型。

- **Type Parameters**: `<C>` — 上下文的类型，`<R>` — 响应的类型
- **Returns**: `Pipeline<C, R>` — 一个新的 Pipeline 实例
