# DeadLetterMessage

> 死信消息包装器，记录被移入死信队列的原始消息及失败原因。

- **Type**: class
- **Package**: `com.euonia.bus.dlq`
- **Author**: damon(zhaorong@outlook.com)

## Constructors

### `DeadLetterMessage(MessageEnvelope<T> originalMessage, Throwable error)`
> 构造方法，创建一个新的死信消息实例。

**Parameters:**
- `originalMessage` (`MessageEnvelope<T>`): 原始消息
- `error` (`Throwable`): 异常信息

## Methods

### `getOriginalMessage(): MessageEnvelope<T>`
> 获取原始消息。

**Returns:** `MessageEnvelope<T>` — 原始消息

### `getReason(): String`
> 获取失败原因。

**Returns:** `String` — 失败原因

### `getExceptionType(): String`
> 获取异常类型名称。

**Returns:** `String` — 异常类型名称

### `getExceptionMessage(): String`
> 获取异常详细信息。

**Returns:** `String` — 异常详细信息

### `getTimestamp(): long`
> 获取移入死信队列的时间戳。

**Returns:** `long` — 时间戳

### `toString(): String`
> 返回死信消息的字符串表示，包含消息ID、失败原因和时间戳。

**Returns:** `String` — 字符串表示
