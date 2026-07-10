# KafkaQueueConsumer

> Kafka 队列消费者，实现单播消息的消费。

- **Type**: `final class` (package-private)
- **Package**: `com.euonia.bus`
- **Extends**: `KafkaRecipient`
- **Implements**: `Consumer`

## Fields

| Name | Type | Description |
|------|------|-------------|
| `consumer` | `KafkaConsumer<String, byte[]>` | Kafka 消费者实例 |
| `replyProducer` | `KafkaProducer<String, byte[]>` | 回复消息的生产者实例 |

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `KafkaQueueConsumer` | `KafkaQueueConsumer(KafkaBusOptions options, HandlerContext handler, MessageSerializer serializer, Class<?> messageType)` | 构造器 |
| `start` | `void start(String channelName)` | 启动消费者，订阅 topic 并轮询消息；收到消息后异步调用 handler，完成后发送回复并触发确认事件 |
| `createConsumer` | `KafkaConsumer<String, byte[]> createConsumer(String channelName)` | 根据 options 创建 Kafka 消费者 |
| `close` | `void close()` | 关闭消费者和回复生产者 |
| `createReplyProducer` | `KafkaProducer<String, byte[]> createReplyProducer()` | 创建回复消息的生产者 |
| `sendReply` | `void sendReply(KafkaProducer<String, byte[]> producer, ConsumerRecord<String, byte[]> request, MessageEnvelope<?> message, Object result, Throwable error)` | 发送回复消息到指定的 replyTo topic；根据处理结果（异常/消息/void）设置不同的类型标记 |
