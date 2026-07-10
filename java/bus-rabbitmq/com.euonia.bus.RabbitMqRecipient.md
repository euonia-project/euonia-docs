# RabbitMqRecipient

> RabbitMQ 消息接收者的抽象基类，封装了与 RabbitMQ 交互的公共逻辑。提供消息接收/确认事件的监听器管理、消息异步处理以及 AMQP 回复属性构建等公共功能。子类需实现 `start(String)` 方法以启动具体的消费模式，以及 `stop()` 方法来停止监听并释放资源。实现 `AutoCloseable`，调用 `close()` 将：①调用 `stop()` 停止消息监听并关闭 Channel ②清除所有已注册的事件监听器。

- **Type:** `public abstract class` implements `AutoCloseable`
- **Package:** `com.euonia.bus`
- **Author:** damon(zhaorong@outlook.com)

## Fields

| Name | Type | Description |
|------|------|-------------|
| `connection` | `protected final Connection` | RabbitMQ 连接 |
| `options` | `protected final RabbitMqBusOptions` | RabbitMQ 总线选项 |
| `handler` | `protected final HandlerContext` | 处理器上下文，用于将消息分派到已注册的处理器 |
| `serializer` | `protected final MessageSerializer` | 消息序列化器 |
| `messageType` | `protected final Class<?>` | 此接收者处理的消息类型 |
| `messageReceivedListeners` | `private final List<Consumer<MessageReceivedEvent>>` | 消息接收事件监听器列表 |
| `messageAcknowledgedListeners` | `private final List<Consumer<MessageAcknowledgedEvent>>` | 消息确认事件监听器列表 |

## Methods

| Name | Return | Description |
|------|--------|-------------|
| `RabbitMqRecipient(Connection, RabbitMqBusOptions, HandlerContext, MessageSerializer, Class<?>)` | (constructor) | 使用必要的依赖构造 RabbitMQ 接收者 |
| `onMessageReceived(Consumer<MessageReceivedEvent>)` | `void` | 注册消息接收事件监听器。当从 RabbitMQ 接收到消息时，监听器将被通知 |
| `onMessageAcknowledged(Consumer<MessageAcknowledgedEvent>)` | `void` | 注册消息确认事件监听器。当消息被确认（ack）时，监听器将被通知 |
| `raiseMessageReceived(MessageReceivedEvent)` | `protected void` | 触发消息接收事件，通知所有已注册的消息接收监听器 |
| `raiseMessageAcknowledged(MessageAcknowledgedEvent)` | `protected void` | 触发消息确认事件，通知所有已注册的消息确认监听器 |
| `start(String)` | `abstract void` | 启动接收者，开始监听指定通道的消息 |
| `stop()` | `protected abstract void` | 停止接收者，取消消费者并关闭 Channel。实现应：①调用 `basicCancel(consumerTag)` 停止投递 ②调用 `channel.close()` 释放 Channel 资源。此方法可能被多次调用，实现应为幂等的 |
| `close()` | `void` | 关闭此接收者，停止消息监听并清除所有事件监听器。此方法可安全地多次调用 |
| `getName()` | `String` | 返回接收者的名称，默认为当前类的简单名称 |
| `createReplyProperties(String, RabbitMqReplyType)` | `AMQP.BasicProperties` | 创建带有关联 ID 和回复类型的 AMQP 回复属性（contentType: application/json） |
| `declareDeadLetterInfrastructure(Channel, String)` | `Map<String, Object>` | 声明死信交换器和死信队列（如已启用），并返回应传递给主队列声明的 AMQP 参数（`x-dead-letter-exchange` 和 `x-dead-letter-routing-key`）。使用 FANOUT 交换器类型 |
