# IncomingLoggingBehavior

> IncomingLoggingBehavior 是一个用于记录入站消息的行为类，实现了 PipelineBehavior 接口。
> 它在消息通过管道接收之前，记录消息的内容，以便进行调试和监控。

- **Module**: `bus-core`
- **Type**: `final class`
- **Package**: `com.euonia.bus.behavior`

## Type Parameters

| Parameter | Bound | Description |
|-----------|-------|-------------|
| `T` | *(无)* | 消息类型 |
| `R` | *(无)* | 响应类型 |

## Methods

### handleAsync

> （未提供注释）

- **Parameters**:
  - `context` (`RoutedMessage&lt;T&gt;`): 路由消息上下文
  - `next` (`PipelineDelegate&lt;RoutedMessage&lt;T&gt;, R&gt;`): 管道委托
- **Returns**: `CompletionStage&lt;R&gt;` - 处理结果

## Usage

```java
Pipeline<RoutedMessage<MyMessage>, MyResponse> pipeline = ...;
pipeline.use(IncomingLoggingBehavior.class);
```
