# RabbitMqReplyType

> RabbitMQ 回复类型枚举，用于标识 AMQP 回复消息的类型。

- **Type:** `enum` (package-private)
- **Package:** `com.euonia.bus`

## Enum Constants

| Name | Value | Description |
|------|-------|-------------|
| `EXCEPTION` | `"EXCEPTION"` | 异常回复 |
| `EMPTY` | `"EMPTY"` | 空回复 |
| `MESSAGE` | `"MESSAGE"` | 消息回复 |

## Fields

| Name | Type | Description |
|------|------|-------------|
| `value` | `private final String` | 回复类型的字符串值 |

## Methods

| Name | Return | Description |
|------|--------|-------------|
| `RabbitMqReplyType(String)` | (constructor) | 使用给定字符串值构造枚举实例 |
| `getValue()` | `String` | 获取回复类型的字符串值 |
