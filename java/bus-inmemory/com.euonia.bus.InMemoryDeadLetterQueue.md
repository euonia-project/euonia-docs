# InMemoryDeadLetterQueue

> 内存死信队列，按通道路由存储处理失败的消息。单例模式，与 `InMemoryTransport` 生命周期绑定。调用 `reset()` 可清空所有死信消息。

- **Type**: `final class`
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Name | Type | Modifiers | Description |
|------|------|-----------|-------------|
| `INSTANCE` | `InMemoryDeadLetterQueue` | `private static final` | 单例实例。 |
| `store` | `ConcurrentMap<String, List<DeadLetterMessage<?>>>` | `private final` | 按通道存储死信消息的映射。 |

## Methods

| Name | Return Type | Parameters | Description |
|------|-------------|------------|-------------|
| `getInstance` | `InMemoryDeadLetterQueue` | — | 获取单例实例。 |
| `publish` | `void` | `String channel, DeadLetterMessage<?> message` | 将死信消息存储到指定通道。 |
| `getDeadLetters` | `List<DeadLetterMessage<?>>` | `String channel` | 获取指定通道的所有死信消息（不移除）。 |
| `size` | `int` | — | 获取所有通道的死信消息计数。 |
| `reset` | `void` | — | 清空所有通道的死信消息。 |
