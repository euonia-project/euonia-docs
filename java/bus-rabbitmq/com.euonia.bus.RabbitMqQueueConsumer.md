# RabbitMqQueueConsumer

> RabbitMQ 队列消费者，实现单播消息的消费。从指定队列消费消息，异步处理后将回复（如有）发送回调用者声明的 `replyTo` 队列。支持基于 correlationId 的请求-响应匹配。

- **Type:** `final class` extends `RabbitMqRecipient` implements `Consumer`
- **Package:** `com.euonia.bus`
- **Author:** damon(zhaorong@outlook.com)

## Fields

| Name | Type | Description |
|------|------|-------------|
| `channel` | `Channel` | RabbitMQ 通道，用于队列操作 |
| `recipientTag` | `String` | 消费者标签，用于取消订阅 |

## Methods

| Name | Return | Description |
|------|--------|-------------|
| `RabbitMqQueueConsumer(Connection, RabbitMqBusOptions, HandlerContext, MessageSerializer, Class<?>)` | (constructor) | 使用必要的依赖构造队列消费者 |
| `start(String)` | `void` | 启动队列消费，声明持久队列并开始监听消息。收到消息后：①反序列化消息体 ②触发消息接收事件 ③异步处理消息 ④如果请求包含 correlationId 和 replyTo，将处理结果或异常发送回回复队列 |
| `stop()` | `void` | 停止接收者，取消消费者并关闭 Channel。如果 recipientTag 不为 null，调用 `basicCancel`；然后关闭 channel |
