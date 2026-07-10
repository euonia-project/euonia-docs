# StrongReferenceMessenger

> `Messenger` 的强引用实现。此 Messenger 使用强引用来跟踪已注册的接收者。当不再需要接收者时，**必须**手动取消注册以避免内存泄漏。**线程安全**：所有公开方法都是线程安全的。

- **Type**: `final class` (implements `Messenger`)
- **Package**: `com.euonia.bus.messenger`
- **Author**: damon(zhaorong@outlook.com)
- **See**: `WeakReferenceMessenger`

## Fields

| Name | Type | Modifiers | Description |
|------|------|-----------|-------------|
| `DEFAULT` | `StrongReferenceMessenger` | `private static final` | 默认单例实例。 |
| `handlers` | `ConcurrentHashMap<Class<?>, ConcurrentHashMap<String, ConcurrentHashMap<RecipientKey, MessageHandlerDispatcher>>>` | `private final` | 所有已注册的处理器：消息类 → 通道 → （接收者 → 分发器）。 |
| `recipientKeys` | `ConcurrentHashMap<RecipientKey, Set<MessageChannelKey>>` | `private final` | 跟踪每个接收者注册了哪些 (消息类, 通道) 对，以便 `unregisterAll` 可以高效扫描。 |

## Methods

| Name | Return Type | Parameters | Description |
|------|-------------|------------|-------------|
| `getDefault` | `StrongReferenceMessenger` | — | 获取默认单例实例。 |
| `isRegistered` | `<TMessage> boolean` | `Object recipient, Class<TMessage> messageType` | 检查接收者在默认通道上是否为指定的消息类型注册了处理器。 |
| `isRegistered` | `<TMessage> boolean` | `Object recipient, Class<TMessage> messageType, String channel` | 检查接收者在指定通道上是否为给定的消息类型注册了处理器。 |
| `register` | `<TRecipient, TMessage> void` | `TRecipient recipient, Class<TMessage> messageType, MessageHandler<TRecipient, TMessage> handler` | 在默认通道上为接收者注册特定消息类型的处理器。 |
| `register` | `<TRecipient, TMessage> void` | `TRecipient recipient, Class<TMessage> messageType, String channel, MessageHandler<TRecipient, TMessage> handler` | 在指定通道上为接收者注册特定消息类型的处理器。 |
| `register` | `<TMessage> void` | `Recipient<TMessage> recipient, Class<TMessage> messageType` | 在默认通道上为实现了 `Recipient` 的接收者注册消息类型（快速路径，NULL 标记）。 |
| `register` | `<TMessage> void` | `Recipient<TMessage> recipient, Class<TMessage> messageType, String channel` | 在指定通道上为实现了 `Recipient` 的接收者注册消息类型（快速路径，NULL 标记）。 |
| `send` | `<TMessage> TMessage` | `TMessage message` | 向默认通道上所有已注册的接收者发送消息。 |
| `send` | `<TMessage> TMessage` | `TMessage message, String channel` | 向指定通道上所有已注册的接收者发送消息。创建处理器快照，NULL 分发器走快速路径直接调用 `Recipient.receive()`。 |
| `unregisterAll` | `void` | `Object recipient` | 在所有通道上取消注册接收者的所有消息类型。 |
| `unregisterAll` | `void` | `Object recipient, String channel` | 在指定通道上取消注册接收者的所有消息类型。默认通道上抛出 `UnsupportedOperationException`，建议使用 `unregisterAll(Object)`。 |
| `unregister` | `<TMessage> void` | `Object recipient, Class<TMessage> messageType` | 在默认通道上取消注册接收者的特定消息类型。 |
| `unregister` | `<TMessage> void` | `Object recipient, Class<TMessage> messageType, String channel` | 在指定通道上取消注册接收者的特定消息类型。 |
| `cleanup` | `void` | — | 强引用不需要清理——所有注册都是显式的。 |
| `reset` | `void` | — | 重置消息传递器，取消注册所有接收者。 |

### Inner Types

| Name | Type | Description |
|------|------|-------------|
| `MessageChannelKey` | `private record` | 标识特定 (消息类型, 通道) 注册对的复合键。 |
| `RecipientKey` | `private static final class` | 包装接收者对象以用作映射键。使用基于身份相等性的比较（`==`），使得即使两个不同的对象 `.equals()` 为 true，它们仍会被视为不同的接收者。 |
