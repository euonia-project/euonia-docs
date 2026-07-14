# HandlerContext

> 定义消息处理器上下文的契约。
>
> 处理器上下文负责管理消息处理器的注册和消息的异步分发。
> 支持消息订阅事件监听，以及基于消息类型或指定通道的异步消息处理。

- **Type**: interface
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### `onMessageSubscribed(Consumer<MessageSubscribedEvent> listener): void`

> 添加消息订阅事件的监听器。

**Parameters:**
- `listener` (`Consumer<MessageSubscribedEvent>`): 当消息被订阅时要调用的消费者

### `handleAsync(String channel, String recipient, MessageEnvelope<?> envelope, MessageContext context): CompletableFuture<Object>`

> 在指定通道上异步处理消息，并指定接收者。

**Parameters:**
- `channel` (`String`): 通道名称
- `recipient` (`String`): 接收者标识
- `envelope` (`MessageEnvelope<?>`): 消息封装
- `context` (`MessageContext`): 消息上下文

**Returns:** `CompletableFuture<Object>` — 表示操作待完成的 CompletableFuture
