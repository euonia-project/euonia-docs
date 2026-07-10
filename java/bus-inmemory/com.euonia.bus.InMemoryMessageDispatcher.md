# InMemoryMessageDispatcher

> 单例内存消息分发器，用于将 `MessagePack` 对象按通道路由到已注册的处理器。此类替代了原始 `InMemoryTransport` 实现中使用的 .NET `StrongReferenceMessenger` / `WeakReferenceMessenger` 模式。处理器以强引用方式存储——调用者负责在不再需要处理器时取消注册。

- **Type**: `final class`
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Name | Type | Modifiers | Description |
|------|------|-----------|-------------|
| `INSTANCE` | `InMemoryMessageDispatcher` | `private static final` | 单例实例。 |
| `channelHandlers` | `Map<String, List<Consumer<MessagePack>>>` | `private final` | 按通道存储的处理器列表。 |

## Methods

| Name | Return Type | Parameters | Description |
|------|-------------|------------|-------------|
| `getInstance` | `InMemoryMessageDispatcher` | — | 获取单例分发器实例。 |
| `register` | `void` | `String channel, Consumer<MessagePack> handler` | 为指定通道注册一个处理器。 |
| `unregister` | `void` | `String channel, Consumer<MessagePack> handler` | 从指定通道取消注册一个处理器。 |
| `dispatch` | `void` | `MessagePack pack` | 将消息包分发到该消息对应通道的所有已注册处理器。每个处理器都会被同步调用。如果处理器抛出异常，该异常会传播给调用者。 |
| `reset` | `void` | — | 移除所有通道的所有已注册处理器。 |
