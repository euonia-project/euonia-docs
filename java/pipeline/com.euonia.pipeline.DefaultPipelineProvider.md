# DefaultPipelineProvider

> DefaultPipelineProvider 是 Pipeline 的具体实现，使用反射来调用管道行为。它同时支持同步和异步的 handle 方法，以及实现了 PipelineBehavior 接口的行为。

- **Type**: class
- **Package**: `com.euonia.pipeline`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<C>` — 请求/上下文对象的类型，`<R>` — 响应对象的类型
- **Extends**: `PipelineBase<C, R>`

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `HANDLE_METHOD_NAME` | `static final String` | 同步处理方法名：`"handle"` |
| `HANDLE_METHOD_NAME_ASYNC` | `static final String` | 异步处理方法名：`"handleAsync"` |
| `provider` | `ServiceProvider` | 服务提供者，用于解析和创建行为实例 |

## Methods

### DefaultPipelineProvider (constructor)

> 使用指定的服务提供者构造管道提供者。

- **Parameters**:
  - `provider` (`ServiceProvider`): 服务提供者

### getNext

> 获取下一个管道委托。如果行为类型实现了 PipelineBehavior 接口，则直接调用其异步处理方法；否则使用反射查找 handle/handleAsync 方法进行调用。

- **Parameters**:
  - `next` (`PipelineDelegate<C, R>`): 链中的下一个委托
  - `behaviorType` (`Class<?>`): 行为类型
  - `constructorArguments` (`Object...`): 构造参数，next 委托会被自动添加到参数列表开头
- **Returns**: `PipelineDelegate<C, R>` — 包装了行为调用的管道委托
