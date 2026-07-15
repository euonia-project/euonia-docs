# IncomingLoggingBehavior

> IncomingLoggingBehavior 是一个用于记录入站消息的行为类，实现了 PipelineBehavior 接口。
> 它在消息通过管道接收之前，记录消息的内容，以便进行调试和监控。

- **Module**: `bus-core`
- **Type**: `final class`
- **Package**: `com.euonia.bus.behavior`

- **Author**: damon(zhaorong@outlook.com)

## Type Parameters

| Parameter | Bound | Description |
|-----------|-------|-------------|
| `T` | *(无)* | 消息类型 |
| `R` | *(无)* | 响应类型 |

## Methods

### handleAsync

> （未提供注释）

- **Parameters**:
  - `context` (`MessageEnvelope<T>`): 路由消息上下文
  - `next` (`PipelineDelegate<MessageEnvelope<T>, R>`): 管道委托
- **Returns**: `CompletionStage<R>` - 处理结果

## Usage

```java
Pipeline<MessageEnvelope<MyMessage>, MyResponse> pipeline = ...;
pipeline.use(IncomingLoggingBehavior.class);
```
