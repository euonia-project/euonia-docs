# EquatableType

> 表示消息类型与其令牌（通道）类型键的不可变二元组。用作类型字典中的复合键，以查找特定消息/令牌类型组合的已注册处理器。

- **Type**: `final class`
- **Package**: `com.euonia.bus.messenger`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Name | Type | Modifiers | Description |
|------|------|-----------|-------------|
| `messageType` | `Class<?>` | `private final` | 消息类型。 |
| `tokenType` | `Class<?>` | `private final` | 令牌（通道）类型。 |

## Methods

| Name | Return Type | Parameters | Description |
|------|-------------|------------|-------------|
| `EquatableType` *(constructor)* | — | `Class<?> messageType, Class<?> tokenType` | 使用指定的消息类型和令牌类型构造新实例。 |
| `getMessageType` | `Class<?>` | — | 获取消息类型。 |
| `getTokenType` | `Class<?>` | — | 获取令牌（通道）类型。 |
| `equals` | `boolean` | `Object obj` | 基于消息类型和令牌类型的引用相等性进行比较。 |
| `hashCode` | `int` | — | 使用 djb2 算法组合消息类型和令牌类型的哈希码。 |
| `toString` | `String` | — | 返回包含消息类型和令牌类型名称的字符串表示。 |
