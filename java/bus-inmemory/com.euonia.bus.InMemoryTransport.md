# InMemoryTransport

> 使用内存消息传递的 `Transport` 实现。消息通过 `Messenger`（默认为 `StrongReferenceMessenger`）进行分发，将 `MessagePack` 实例按通道路由到已注册的处理器。生命周期：实现 `AutoCloseable` 接口——调用 `close()` 来重置底层 messenger（通常由 DI 容器管理）。

- **Type**: `class` (implements `Transport`, `AutoCloseable`)
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Name | Type | Modifiers | Description |
|------|------|-----------|-------------|
| `LOGGER` | `Logger` | `private static final` | 日志记录器。 |
| `name` | `String` | `private final` | 传输实例名称。 |
| `deliveredListeners` | `List<Consumer<MessageDeliveredEvent>>` | `private final` | 消息已送达事件的监听器列表，使用写时复制策略以保证线程安全。 |

## Methods

| Name | Return Type | Parameters | Description |
|------|-------------|------------|-------------|
| `InMemoryTransport` *(constructor)* | — | `InMemoryBusOptions options` | 使用指定的配置选项初始化新实例，使用默认的 `StrongReferenceMessenger` 单例。 |
| `getName` | `String` | — | 获取传输实例名称。 |
| `publishAsync` | `<M> CompletableFuture<Void>` | `MessageEnvelope<M> message` | 以即发即忘的方式发布消息。返回的 future 在分发后立即完成——不等待任何确认。 |
| `sendAsync` | `<M> CompletableFuture<Void>` | `MessageEnvelope<M> message` | 发送一条命令消息并等待完成（或失败）。 |
| `sendAsync` | `<M, R> CompletableFuture<R>` | `MessageEnvelope<M> message, Class<R> responseType` | 发送一条请求消息并期待一个类型化的响应。 |
| `callAsync` | `<M, R> CompletableFuture<R>` | `MessageEnvelope<M> message, Class<R> responseType` | 发送一条请求消息并期待一个响应。便利的重载方法，不指定编译时的期望响应类型。 |
| `addDeliveredListener` | `void` | `Consumer<MessageDeliveredEvent> listener` | 注册消息已送达事件的监听器。 |
| `removeDeliveredListener` | `void` | `Consumer<MessageDeliveredEvent> listener` | 取消注册消息已送达事件的监听器。 |
| `fireDelivered` | `void` | `Object payload, MessageContext context` | 触发消息已送达事件。 |
| `close` | `void` | — | 重置底层 messenger，清除所有已注册的处理器。对应 .NET 的 `Dispose` 模式。 |
