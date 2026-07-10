# RabbitMqRequestExecutor

> RabbitMQ RPC 请求执行器，实现请求-响应模式的消息消费。从 RPC 队列消费消息，异步处理后将结果（成功响应或异常）通过调用者声明的 `replyTo` 队列返回。与 `RabbitMqQueueConsumer` 相比，此执行器使用 `DeliverCallback` 而非 `DefaultConsumer`。

- **Type:** `final class` extends `RabbitMqRecipient` implements `Executor`
- **Package:** `com.euonia.bus`
- **Author:** damon(zhaorong@outlook.com)

## Fields

| Name | Type | Description |
|------|------|-------------|
| `channel` | `Channel` | RabbitMQ 通道，用于 RPC 队列操作 |
| `recipientTag` | `String` | 消费者标签，用于取消订阅 |

## Methods

| Name | Return | Description |
|------|--------|-------------|
| `RabbitMqRequestExecutor(Connection, RabbitMqBusOptions, HandlerContext, MessageSerializer, Class<?>)` | (constructor) | 使用必要的依赖构造 RPC 请求执行器 |
| `start(String)` | `void` | 启动 RPC 请求执行，声明持久队列并开始监听消息。收到消息后：①反序列化消息体 ②触发消息接收事件 ③异步处理消息 ④将处理结果（成功响应或异常）通过 replyTo 队列返回给调用者。使用 `DeliverCallback` 进行消息投递回调 |
| `stop()` | `void` | 停止执行器，取消消费者并关闭 Channel |
