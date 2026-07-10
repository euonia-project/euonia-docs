# InMemoryUnicastRecipient

> 内存消息总线的单播（点对点）消息接收者。继承自 `InMemoryRecipient`，实现 `Consumer` 接口，用于处理单播类型的消息。通过 `HandlerContext` 将消息分发给实际的消息处理器，并在处理完成后将任何异常记录到日志中（不会中断消息处理）。

- **Type**: `class` (extends `InMemoryRecipient`, implements `Consumer`)
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Fields

*(No additional fields beyond those inherited from `InMemoryRecipient`)*

## Methods

| Name | Return Type | Parameters | Description |
|------|-------------|------------|-------------|
| `InMemoryUnicastRecipient` *(constructor)* | — | `HandlerContext handler` | 创建单播接收者实例。 |
| `getName` | `String` | — | 获取接收者名称。返回接收者的简单类名。 |
