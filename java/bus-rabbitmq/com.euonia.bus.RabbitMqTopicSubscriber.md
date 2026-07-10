# RabbitMqTopicSubscriber

> RabbitMQ 主题订阅者，实现多播消息的消费。绑定到扇出（fanout）交换器，声明独占队列并消费所有发布到该交换器的消息。消息处理完成后自动发送 ACK 确认并触发消息确认事件。

- **Type:** `final class` extends `RabbitMqRecipient` implements `Subscriber`
- **Package:** `com.euonia.bus`
- **Author:** damon(zhaorong@outlook.com)

## Fields

| Name | Type | Description |
|------|------|-------------|
| `channel` | `Channel` | RabbitMQ 通道，用于交换器和队列操作 |
| `recipientTag` | `String` | 消费者标签，用于取消订阅 |

## Methods

| Name | Return | Description |
|------|--------|-------------|
| `RabbitMqTopicSubscriber(Connection, RabbitMqBusOptions, HandlerContext, MessageSerializer, Class<?>)` | (constructor) | 使用必要的依赖构造主题订阅者 |
| `start(String)` | `void` | 启动主题订阅，声明扇出交换器（FANOUT）和独占队列，绑定（routing key: `*`）后开始监听消息。收到消息后：①反序列化消息体 ②触发消息接收事件 ③异步处理消息 ④处理完成后发送 ACK 确认并触发消息确认事件 |
| `stop()` | `void` | 停止订阅者，取消消费者并关闭 Channel |
