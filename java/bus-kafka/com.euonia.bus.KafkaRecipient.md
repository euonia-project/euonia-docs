# KafkaRecipient

> Kafka 消息接收者的抽象基类。

- **Type**: `public abstract class`
- **Package**: `com.euonia.bus`
- **Author**: `damon(zhaorong@outlook.com)`
- **Implements**: `AutoCloseable`

## Fields

| Name | Type | Description |
|------|------|-------------|
| `LOGGER` | `Logger` | 日志记录器 |
| `options` | `KafkaBusOptions` | Kafka 总线配置选项 |
| `handler` | `HandlerContext` | 消息处理器上下文 |
| `serializer` | `MessageSerializer` | 消息序列化器 |
| `messageType` | `Class<?>` | 消息类型 |
| `messageReceivedListeners` | `List<Consumer<MessageReceivedEvent>>` | 消息接收事件监听器列表 |
| `messageAcknowledgedListeners` | `List<Consumer<MessageAcknowledgedEvent>>` | 消息确认事件监听器列表 |

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `KafkaRecipient` | `protected KafkaRecipient(KafkaBusOptions options, HandlerContext handler, MessageSerializer serializer, Class<?> messageType)` | 构造器 |
| `onMessageReceived` | `void onMessageReceived(Consumer<MessageReceivedEvent> listener)` | 注册消息接收事件监听器 |
| `onMessageAcknowledged` | `void onMessageAcknowledged(Consumer<MessageAcknowledgedEvent> listener)` | 注册消息确认事件监听器 |
| `raiseMessageReceived` | `void raiseMessageReceived(MessageReceivedEvent event)` | 触发消息接收事件，通知所有已注册的监听器 |
| `raiseMessageAcknowledged` | `void raiseMessageAcknowledged(MessageAcknowledgedEvent event)` | 触发消息确认事件，通知所有已注册的监听器 |
| `start` | `abstract void start(String channelName)` | 启动接收者（由子类实现） |
| `getName` | `String getName()` | 获取接收者名称（默认为类名） |
| `close` | `void close()` | 关闭接收者，记录日志 |
