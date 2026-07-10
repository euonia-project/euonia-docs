# MessageHandlerDispatcher

> 抽象分发器，在目标接收者上使用给定的消息调用 `MessageHandler` 回调。使用抽象类分发（虚方法）而非接口分发以获得更好的性能。包含两个子类：`For` — 包装类型化的 `MessageHandler`；`NullDispatcher` — 标记接收者实现了 `Recipient` 接口。

- **Type**: `abstract class`
- **Package**: `com.euonia.bus.messenger`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Name | Type | Modifiers | Description |
|------|------|-----------|-------------|
| `NULL` | `MessageHandlerDispatcher` | `static final` | 单例标记分发器，表示接收者实现了 `Recipient` 接口，应直接通过 `Recipient.receive()` 进行调用。 |

## Methods

| Name | Return Type | Parameters | Description |
|------|-------------|------------|-------------|
| `invoke` | `void` | `Object recipient, Object message` | 在指定的接收者上使用给定的消息调用处理器（抽象方法）。 |

### Inner Class: `For<TRecipient, TMessage>`

| Name | Return Type | Parameters | Description |
|------|-------------|------------|-------------|
| `For` *(constructor)* | — | `MessageHandler<TRecipient, TMessage> handler` | 使用指定的处理器构造新实例。 |
| `invoke` | `void` | `Object recipient, Object message` | 在指定的接收者上使用给定的消息调用处理器。 |
| `getHandler` | `MessageHandler<TRecipient, TMessage>` | — | 获取底层消息处理器。 |
