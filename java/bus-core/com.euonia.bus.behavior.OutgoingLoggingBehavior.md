# OutgoingLoggingBehavior

> OutboundLoggingBehavior 是一个用于记录出站消息的行为类，实现了 PipelineBehavior 接口。
> 它在消息通过管道发送之前，记录消息的 ID、类型、传输方式和通道信息，以便进行调试和监控。

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

### OutgoingLoggingBehavior (constructor)

> 创建一个新的 OutboundLoggingBehavior 实例。

- **Parameters**:
  - `messageType` (`Class&lt;T&gt;`): 消息类型
  - `transportName` (`String`): 传输名称

### handleAsync

> （未提供注释）

- **Parameters**:
  - `context` (`RoutedMessage&lt;T&gt;`): 路由消息上下文
  - `next` (`PipelineDelegate&lt;RoutedMessage&lt;T&gt;, R&gt;`): 管道委托
- **Returns**: `CompletionStage&lt;R&gt;` - 处理结果

## Usage

```java
Pipeline<RoutedMessage<MyMessage>, MyResponse> pipeline = ...;
pipeline.use(OutboundLoggingBehavior.class, "MyTransport");
```
