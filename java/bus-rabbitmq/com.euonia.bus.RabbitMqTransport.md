# RabbitMqTransport

> RabbitMQ 传输实现，负责通过 RabbitMQ 代理发布、发送和调用消息。支持三种消息发送模式：`publishAsync`（多播发布到扇出交换器）、`sendAsync`（单播发送到指定队列并等待响应）、`callAsync`（RPC 调用并等待响应）。内置基于 Failsafe 的重试策略，处理 IOException 和 TimeoutException。

- **Type:** `public final class` implements `Transport`
- **Package:** `com.euonia.bus`
- **Author:** damon(zhaorong@outlook.com)

## Fields

| Name | Type | Description |
|------|------|-------------|
| `connection` | `private final Connection` | RabbitMQ 连接 |
| `serializer` | `private final MessageSerializer` | 消息序列化器 |
| `options` | `private final RabbitMqBusOptions` | RabbitMQ 总线选项 |
| `retryPolicy` | `private final RetryPolicy<Object>` | 基于 Failsafe 的重试策略 |

## Methods

| Name | Return | Description |
|------|--------|-------------|
| `RabbitMqTransport(Connection, MessageSerializer, RabbitMqBusOptions)` | (constructor) | 使用必要的依赖构造 RabbitMQ 传输实例 |
| `getName()` | `String` | 返回传输名称（当前类的简单名称） |
| `publishAsync(MessageEnvelope<M>)` | `<M> CompletableFuture<Void>` | 以多播模式发布消息到扇出（fanout）交换器。交换器名称格式为 `{exchangePrefix}:{channel}`。发布操作受重试策略保护 |
| `sendAsync(MessageEnvelope<M>)` | `<M> CompletableFuture<Void>` | 以单播模式发送消息到指定队列，不等待响应 |
| `sendAsync(MessageEnvelope<M>, Class<R>)` | `<M, R> CompletableFuture<R>` | 以单播模式发送消息到指定队列，并等待指定类型的响应。创建临时回复队列，发布消息后等待匹配 correlationId 的响应。内置超时保护和取消回调处理 |
| `callAsync(MessageEnvelope<M>, Class<R>)` | `<M, R> CompletableFuture<R>` | 以 RPC 模式调用消息，发送请求到指定队列并等待响应。与 `sendAsync` 相比，额外设置了 AMQP `replyTo` 属性，使服务端可以将响应发送回调用者声明的临时队列 |
| `getResponseTimeout()` | `private long` | 基于重试策略参数计算响应超时时间。计算方式为 `retryDelay * (retryAttempts + 1)` 加上 5 秒缓冲用于处理器处理和网络延迟 |
| `closeChannel(Channel)` | `private void` | 安全地关闭通道，记录任何错误但不传播异常 |
| `cancelConsumer(Channel, String)` | `private void` | 安全地取消消费者，记录任何错误但不传播异常 |
| `checkQueue(Channel, String, String)` | `private String` | 检查指定队列是否存在，并且至少有一个消费者在监听。如果队列不存在或没有消费者，抛出 `MessageDeliverException` |
| `createRetryPolicy()` | `private RetryPolicy<Object>` | 创建基于 Failsafe 的重试策略。处理 IOException 和 TimeoutException，使用配置的延迟和最大重试次数 |
