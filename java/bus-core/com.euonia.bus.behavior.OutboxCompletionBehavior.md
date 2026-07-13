# OutboxCompletionBehavior

> OutboxCompletionBehavior 是一个管道行为，用于在消息处理完成后更新发件箱状态。
>
> 它在消息处理成功时将消息标记为成功，在处理失败时将消息标记为失败，并记录异常信息。
>
> 该行为依赖于 `OutboxStore` 来持久化消息状态。

- **Module**: `bus-core`
- **Type**: `final class`
- **Package**: `com.euonia.bus.behavior`
- **Author**: damon(zhaorong@outlook.com)

## Type Parameters

| Parameter | Bound | Description |
|-----------|-------|-------------|
| `T` | *(无)* | 消息负载类型 |

## Methods

### OutboxCompletionBehavior (constructor)

> 创建一个新的 OutboxCompletionBehavior 实例。

- **Parameters**:
  - `outboxStore` (`OutboxStore`): 用于持久化消息状态的发件箱存储
  - `transportName` (`String`): 传输名称，用于标识消息的传输方式

### handleAsync

> （未提供注释）

- **Parameters**:
  - `context` (`MessageEnvelope<T>`): 消息信封上下文
  - `next` (`PipelineDelegate<MessageEnvelope<T>, Void>`): 管道委托
- **Returns**: `CompletionStage<Void>` - 处理结果
