# DefaultPipelineFactory

> DefaultPipelineFactory 是 PipelineFactory 的默认实现，负责创建 Pipeline 的实例。它使用 ServiceProvider 来解析和实例化管道组件。

- **Type**: class
- **Package**: `com.euonia.pipeline`
- **Author**: damon(zhaorong@outlook.com)
- **Implements**: `PipelineFactory`

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `provider` | `ServiceProvider` | 用于解析和实例化管道组件的 ServiceProvider |

## Methods

### DefaultPipelineFactory (constructor)

> 构造函数，接受一个 ServiceProvider 实例。

- **Parameters**:
  - `provider` (`ServiceProvider`): 用于解析和实例化管道组件的 ServiceProvider

### create

> 创建一个新的 Pipeline 实例，并指定上下文和响应类型。返回一个基于 DefaultPipelineProvider 的新管道。

- **Type Parameters**: `<C>` — 上下文的类型，`<R>` — 响应的类型
- **Returns**: `Pipeline<C, R>` — 一个新的 Pipeline 实例
