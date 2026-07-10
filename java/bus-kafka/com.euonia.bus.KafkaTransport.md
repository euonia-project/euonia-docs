# KafkaTransport

> Kafka 传输实现，负责通过 Kafka 代理发布、发送和调用消息。

- **Type**: `public final class`
- **Package**: `com.euonia.bus`
- **Author**: `damon(zhaorong@outlook.com)`
- **Implements**: `Transport`, `AutoCloseable`

## Fields

| Name | Type | Description |
|------|------|-------------|
| `LOGGER` | `Logger` | 日志记录器 |
| `producer` | `KafkaProducer<String, byte[]>` | Kafka 生产者实例 |
| `serializer` | `MessageSerializer` | 消息序列化器 |
| `options` | `KafkaBusOptions` | Kafka 总线配置选项 |
| `retryPolicy` | `RetryPolicy<Object>` | 重试策略（处理 IOException / TimeoutException） |

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `KafkaTransport` | `KafkaTransport(KafkaBusOptions options, MessageSerializer serializer)` | 构造器；初始化生产者及重试策略 |
| `getName` | `String getName()` | 获取传输名称（返回类名） |
| `publishAsync` | `<M> CompletableFuture<Void> publishAsync(MessageEnvelope<M> message)` | 异步发布消息到 Kafka topic |
| `sendAsync` | `<M> CompletableFuture<Void> sendAsync(MessageEnvelope<M> message)` | 异步发送消息（委托给 publishAsync） |
| `sendAsync` | `<M, R> CompletableFuture<R> sendAsync(MessageEnvelope<M> message, Class<R> responseType)` | 异步发送消息并等待响应（委托给 callAsync） |
| `callAsync` | `<M, R> CompletableFuture<R> callAsync(MessageEnvelope<M> message, Class<R> responseType)` | 异步 RPC 调用；发送消息后在独立的 reply topic 上等待响应，支持重试 |
| `createReplyConsumer` | `KafkaConsumer<String, byte[]> createReplyConsumer()` | 创建用于接收 RPC 响应的消费者 |
| `createProducer` | `KafkaProducer<String, byte[]> createProducer()` | 创建 Kafka 生产者 |
| `close` | `void close()` | 关闭生产者 |
| `createRetryPolicy` | `RetryPolicy<Object> createRetryPolicy()` | 创建重试策略；处理 IOException 和 TimeoutException，使用 options 中的延迟和重试次数配置 |
