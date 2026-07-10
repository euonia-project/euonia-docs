# Recipient

> 一个通用的消息接收者，可以接收类型为 `TMessage` 的消息。实现此接口的接收者可以通过优化的快速路径（null 分发器标记）注册到 `Messenger`。

- **Type**: `@FunctionalInterface` (type parameter: `<TMessage>`)
- **Package**: `com.euonia.bus.messenger`
- **Author**: damon(zhaorong@outlook.com)

## Fields

*(No fields — functional interface)*

## Methods

| Name | Return Type | Parameters | Description |
|------|-------------|------------|-------------|
| `receive` | `void` | `TMessage message` | 当类型为 `TMessage` 的消息被发送到此接收者时调用。 |
