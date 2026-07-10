# KafkaTopicSubscriber

> Kafka 主题订阅者，实现多播消息的消费。

- **Type**: `final class` (package-private)
- **Package**: `com.euonia.bus`
- **Extends**: `KafkaRecipient`
- **Implements**: `Subscriber`

## Fields

| Name | Type | Description |
|------|------|-------------|
| `consumer` | `KafkaConsumer<String, byte[]>` | Kafka 消费者实例 |

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `KafkaTopicSubscriber` | `KafkaTopicSubscriber(KafkaBusOptions options, HandlerContext handler, MessageSerializer serializer, Class<?> messageType)` | 构造器 |
| `start` | `void start(String channelName)` | 启动订阅者，订阅 topic 并轮询消息；收到消息后异步调用 handler，完成后提交 offset 并触发确认事件 |
| `createConsumer` | `KafkaConsumer<String, byte[]> createConsumer(String channelName)` | 根据 options 创建 Kafka 消费者 |
| `close` | `void close()` | 关闭消费者 |
