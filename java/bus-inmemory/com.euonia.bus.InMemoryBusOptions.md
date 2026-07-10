# InMemoryBusOptions

> 内存消息总线传输的配置选项。

- **Type**: `class`
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Name | Type | Modifiers | Description |
|------|------|-----------|-------------|
| `DEFAULT_TRANSPORT_NAME` | `String` | `public static final` | 默认的传输名称。 |
| `name` | `String` | `private` | 传输名称。 |
| `lazyInitialize` | `boolean` | `private` | 是否启用延迟初始化。 |
| `maxConcurrentCalls` | `int` | `private` | 最大并发调用数。 |
| `multipleSubscriberInstance` | `boolean` | `private` | 是否为每个消息通道创建独立的订阅者实例。 |
| `deadLetterEnabled` | `boolean` | `private` | 是否启用死信队列。启用后，处理失败的消息将被存储到 `InMemoryDeadLetterQueue`。 |

## Methods

| Name | Return Type | Parameters | Description |
|------|-------------|------------|-------------|
| `getName` | `String` | — | 获取传输名称。 |
| `setName` | `void` | `String name` | 设置传输名称。 |
| `isLazyInitialize` | `boolean` | — | 获取是否启用延迟初始化。 |
| `setLazyInitialize` | `void` | `boolean lazyInitialize` | 设置是否启用延迟初始化。 |
| `getMaxConcurrentCalls` | `int` | — | 获取最大并发调用数。 |
| `setMaxConcurrentCalls` | `void` | `int maxConcurrentCalls` | 设置最大并发调用数。 |
| `isMultipleSubscriberInstance` | `boolean` | — | 获取是否为每个消息通道创建独立的订阅者实例。 |
| `setMultipleSubscriberInstance` | `void` | `boolean multipleSubscriberInstance` | 设置是否为每个消息通道创建独立的订阅者实例。 |
| `isDeadLetterEnabled` | `boolean` | — | 获取是否启用死信队列。 |
| `setDeadLetterEnabled` | `void` | `boolean deadLetterEnabled` | 设置是否启用死信队列。 |
