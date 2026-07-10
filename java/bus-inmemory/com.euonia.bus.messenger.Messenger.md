# Messenger

> 定义消息传递器的契约，能够在由令牌标识的各个通道上发送消息以及订阅/取消订阅接收者。

- **Type**: `interface`
- **Package**: `com.euonia.bus.messenger`
- **Author**: damon(zhaorong@outlook.com)
- **See**: `StrongReferenceMessenger`, `WeakReferenceMessenger`

## Fields

| Name | Type | Modifiers | Description |
|------|------|-----------|-------------|
| `DEFAULT_CHANNEL` | `String` | *(implicit `public static final`)* | 默认通道令牌。当不需要指定通道时使用此令牌（空字符串）。 |

## Methods

| Name | Return Type | Parameters | Description |
|------|-------------|------------|-------------|
| `isRegistered` | `<TMessage> boolean` | `Object recipient, Class<TMessage> messageType` | 检查接收者在默认通道上是否为指定的消息类型注册了处理器。 |
| `isRegistered` | `<TMessage> boolean` | `Object recipient, Class<TMessage> messageType, String channel` | 检查接收者在指定通道上是否为给定的消息类型注册了处理器。 |
| `register` | `<TRecipient, TMessage> void` | `TRecipient recipient, Class<TMessage> messageType, MessageHandler<TRecipient, TMessage> handler` | 在默认通道上为接收者注册特定消息类型的处理器。 |
| `register` | `<TRecipient, TMessage> void` | `TRecipient recipient, Class<TMessage> messageType, String channel, MessageHandler<TRecipient, TMessage> handler` | 在指定通道上为接收者注册特定消息类型的处理器。 |
| `register` | `<TMessage> void` | `Recipient<TMessage> recipient, Class<TMessage> messageType` | 在默认通道上为实现了 `Recipient` 的接收者注册消息类型（快速路径）。 |
| `register` | `<TMessage> void` | `Recipient<TMessage> recipient, Class<TMessage> messageType, String channel` | 在指定通道上为实现了 `Recipient` 的接收者注册消息类型（快速路径）。 |
| `send` | `<TMessage> TMessage` | `TMessage message` | 向默认通道上所有已注册的接收者发送消息。 |
| `send` | `<TMessage> TMessage` | `TMessage message, String channel` | 向指定通道上所有已注册的接收者发送消息。 |
| `unregisterAll` | `void` | `Object recipient` | 在所有通道上取消注册接收者的所有消息类型。 |
| `unregisterAll` | `void` | `Object recipient, String channel` | 在指定通道上取消注册接收者的所有消息类型。 |
| `unregister` | `<TMessage> void` | `Object recipient, Class<TMessage> messageType` | 在默认通道上取消注册接收者的特定消息类型。 |
| `unregister` | `<TMessage> void` | `Object recipient, Class<TMessage> messageType, String channel` | 在指定通道上取消注册接收者的特定消息类型。 |
| `cleanup` | `void` | — | 对当前消息传递器执行清理。不会取消注册任何接收者，但可能会修剪内部数据结构。 |
| `reset` | `void` | — | 重置消息传递器，取消注册所有接收者。 |
