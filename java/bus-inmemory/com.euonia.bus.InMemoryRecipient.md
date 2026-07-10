# InMemoryRecipient

> 内存消息接收者的抽象基类。此类实现 `Recipient<MessagePack>` 并提供结构化的消息处理管道：当收到 `MessagePack` 时，触发 `messageReceived` 监听器，调用抽象的 `HandlerContext#handleAsync` 方法，然后触发 `messageAcknowledged` 监听器。

- **Type**: `abstract class` (implements `Recipient<MessagePack>`)
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Name | Type | Modifiers | Description |
|------|------|-----------|-------------|
| `LOGGER` | `Logger` | `private static final` | 日志记录器。 |
| `handler` | `HandlerContext` | `private final` | 处理器上下文。 |
| `messageReceivedListeners` | `CopyOnWriteArrayList<Consumer<MessageReceivedEvent>>` | `private final` | 收到消息时（处理前）通知的监听器列表。 |
| `messageAcknowledgedListeners` | `CopyOnWriteArrayList<Consumer<MessageAcknowledgedEvent>>` | `private final` | 消息确认后（处理完成后）通知的监听器列表。 |
| `deadLetterOptions` | `InMemoryBusOptions` | `private` | 死信队列选项，由 `InMemoryRecipientRegistrar` 在创建后注入。 |
| `currentMessage` | `MessageEnvelope<?>` | `protected volatile` | 当前正在处理的路由消息，由 `receive(MessagePack)` 设置，供子类在 `HandlerContext#handleAsync` 的错误路径中调用 `publishDeadLetter` 时读取。 |

## Methods

| Name | Return Type | Parameters | Description |
|------|-------------|------------|-------------|
| `InMemoryRecipient` *(constructor)* | — | `HandlerContext handler` | 创建接收者实例。 |
| `setDeadLetterOptions` | `void` | `InMemoryBusOptions options` | 设置死信队列选项。由 `InMemoryRecipientRegistrar` 在创建接收者后调用。 |
| `addMessageReceivedListener` | `void` | `Consumer<MessageReceivedEvent> listener` | 添加消息接收事件的监听器。 |
| `removeMessageReceivedListener` | `void` | `Consumer<MessageReceivedEvent> listener` | 移除消息接收事件的监听器。 |
| `addMessageAcknowledgedListener` | `void` | `Consumer<MessageAcknowledgedEvent> listener` | 添加消息确认事件的监听器。 |
| `removeMessageAcknowledgedListener` | `void` | `Consumer<MessageAcknowledgedEvent> listener` | 移除消息确认事件的监听器。 |
| `onMessageReceived` | `void` | `MessageReceivedEvent event` | 触发 `messageReceived` 事件。 |
| `onMessageAcknowledged` | `void` | `MessageAcknowledgedEvent event` | 触发 `messageAcknowledged` 事件。 |
| `receive` | `void` | `MessagePack pack` | 接收消息包并通过管道进行处理。 |
| `publishDeadLetter` | `void` | `String channel, MessageEnvelope<?> message, Throwable error` | 如果启用了死信队列，则将处理失败的消息发布到 `InMemoryDeadLetterQueue`。 |
| `getName` | `String` | — | 获取接收者名称（抽象方法）。 |
