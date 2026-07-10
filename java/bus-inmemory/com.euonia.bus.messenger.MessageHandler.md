# MessageHandler

> 函数式接口，表示由特定接收者类型键控的、给定类型消息的处理器。

- **Type**: `@FunctionalInterface` (extends `BiConsumer<TRecipient, TMessage>`)
- **Package**: `com.euonia.bus.messenger`
- **Author**: damon(zhaorong@outlook.com)

## Fields

*(No fields — functional interface)*

## Methods

| Name | Return Type | Parameters | Description |
|------|-------------|------------|-------------|
| `handle` | `void` | `TRecipient recipient, TMessage message` | 为指定的接收者处理消息。 |
| `accept` | `void` | `TRecipient recipient, TMessage message` | `BiConsumer` 的默认实现，委托给 `handle`。 |
