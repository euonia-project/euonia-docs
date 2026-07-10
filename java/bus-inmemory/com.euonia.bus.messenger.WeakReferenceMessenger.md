# WeakReferenceMessenger

> `Messenger` 的弱引用实现。此 Messenger 使用 `WeakReference` 来跟踪已注册的接收者，因此不再被其他地方引用的接收者将被自动垃圾回收。如果接收者未手动取消注册，这样可以避免内存泄漏。**线程安全**：所有公开方法都是线程安全的。

- **Type**: `final class` (implements `Messenger`)
- **Package**: `com.euonia.bus.messenger`
- **Author**: damon(zhaorong@outlook.com)
- **See**: `StrongReferenceMessenger`

## Fields

| Name | Type | Modifiers | Description |
|------|------|-----------|-------------|
| `DEFAULT` | `WeakReferenceMessenger` | `private static final` | 默认单例实例。 |
| `handlers` | `ConcurrentHashMap<Class<?>, ConcurrentHashMap<String, ConcurrentHashMap<WeakKey, MessageHandlerDispatcher>>>` | `private final` | 所有已注册的处理器：消息类 → 通道 → （弱引用接收者 → 分发器）。使用 `WeakKey` 作为键，以便接收者可以被垃圾回收。 |
| `recipientKeys` | `ConcurrentHashMap<WeakKey, Set<MessageChannelKey>>` | `private final` | 跟踪每个接收者的弱引用，用于清理目的。将接收者身份哈希映射到 (消息类, 通道) 集合，以便批量取消注册。 |

## Methods

| Name | Return Type | Parameters | Description |
|------|-------------|------------|-------------|
| `getDefault` | `WeakReferenceMessenger` | — | 获取默认单例实例。 |
| `isRegistered` | `<TMessage> boolean` | `Object recipient, Class<TMessage> messageType` | 检查接收者在默认通道上是否为指定的消息类型注册了处理器。 |
| `isRegistered` | `<TMessage> boolean` | `Object recipient, Class<TMessage> messageType, String channel` | 检查接收者在指定通道上是否为给定的消息类型注册了处理器。 |
| `register` | `<TRecipient, TMessage> void` | `TRecipient recipient, Class<TMessage> messageType, MessageHandler<TRecipient, TMessage> handler` | 在默认通道上为接收者注册特定消息类型的处理器。 |
| `register` | `<TRecipient, TMessage> void` | `TRecipient recipient, Class<TMessage> messageType, String channel, MessageHandler<TRecipient, TMessage> handler` | 在指定通道上为接收者注册特定消息类型的处理器。 |
| `register` | `<TMessage> void` | `Recipient<TMessage> recipient, Class<TMessage> messageType` | 在默认通道上为实现了 `Recipient` 的接收者注册消息类型（快速路径，NULL 标记）。 |
| `register` | `<TMessage> void` | `Recipient<TMessage> recipient, Class<TMessage> messageType, String channel` | 在指定通道上为实现了 `Recipient` 的接收者注册消息类型（快速路径，NULL 标记）。 |
| `send` | `<TMessage> TMessage` | `TMessage message` | 向默认通道上所有已注册的接收者发送消息。 |
| `send` | `<TMessage> TMessage` | `TMessage message, String channel` | 向指定通道上所有已注册的接收者发送消息。创建处理器快照，跳过已被 GC 回收的接收者。 |
| `unregisterAll` | `void` | `Object recipient` | 在所有通道上取消注册接收者的所有消息类型。 |
| `unregisterAll` | `void` | `Object recipient, String channel` | 在指定通道上取消注册接收者的所有消息类型。默认通道上抛出 `UnsupportedOperationException`，建议使用 `unregisterAll(Object)`。 |
| `unregister` | `<TMessage> void` | `Object recipient, Class<TMessage> messageType` | 在默认通道上取消注册接收者的特定消息类型。 |
| `unregister` | `<TMessage> void` | `Object recipient, Class<TMessage> messageType, String channel` | 在指定通道上取消注册接收者的特定消息类型。 |
| `removeRegistration` | `void` | `MessageChannelKey mck, WeakKey key` | 从内部数据结构中移除特定注册。 |
| `cleanup` | `void` | — | 移除其接收者已被垃圾回收的条目。遍历 `recipientKeys`，收集所有已 GC 回收的弱引用并清理。 |
| `reset` | `void` | — | 重置消息传递器，取消注册所有接收者。 |

### Inner Types

| Name | Type | Description |
|------|------|-------------|
| `MessageChannelKey` | `private record` | 标识特定 (消息类型, 通道) 注册对的复合键。 |
| `WeakKey` | `private static final class` (extends `WeakReference<Object>`) | 基于 `WeakReference` 的映射键，用于包装接收者。相等性和哈希码由被引用对象的身份哈希计算，使用 `System.identityHashCode` 和引用相等性（`==`）。 |
