# InboxCompletionBehavior

> InboxCompletionBehavior 是一个管道行为，用于在消息处理完成后更新收件箱状态。
>
> 它在消息处理成功时将消息标记为成功，在处理失败时将消息标记为失败，并记录异常信息。
>
> 该行为依赖于 `InboxStore` 来持久化消息状态。

- **Module**: `bus-core`
- **Type**: `final class`
- **Package**: `com.euonia.bus.behavior`
- **Author**: damon(zhaorong@outlook.com)

## Type Parameters

| Parameter | Bound | Description |
|-----------|-------|-------------|
| `T` | *(无)* | 消息负载类型 |

## Methods

### InboxCompletionBehavior (constructor)

> 创建一个新的 InboxCompletionBehavior 实例。

- **Parameters**:
  - `inboxStore` (`InboxStore`): 用于持久化消息状态的收件箱存储
  - `handlerName` (`String`): 处理器名称，用于标识消息的处理器

### handleAsync

> （未提供注释）

- **Parameters**:
  - `context` (`MessageEnvelope&lt;T&gt;`): 消息信封上下文
  - `next` (`PipelineDelegate&lt;MessageEnvelope&lt;T&gt;, Object&gt;`): 管道委托
- **Returns**: `CompletionStage&lt;Object&gt;` - 处理结果
