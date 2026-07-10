# DeadLetterMessage

> 死信消息包装器，记录被移入死信队列的原始消息及失败原因。

- **Type**: class
- **Package**: `com.euonia.bus.dlq`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `originalMessage` | `MessageEnvelope<T>` | 原始消息 |
| `reason` | `String` | 失败原因 |
| `exceptionType` | `String` | 异常类型名称 |
| `exceptionMessage` | `String` | 异常详细信息 |
| `timestamp` | `long` | 移入死信队列的时间 |

## Methods

### DeadLetterMessage

> 构造方法，创建一个新的死信消息实例。

- **Parameters**:
  - `originalMessage` (`MessageEnvelope<T>`): 原始消息
  - `error` (`Throwable`): 异常信息

### getOriginalMessage

> 获取原始消息。

- **Returns**: `MessageEnvelope<T>` - 原始消息

### getReason

> 获取失败原因。

- **Returns**: `String` - 失败原因

### getExceptionType

> 获取异常类型名称。

- **Returns**: `String` - 异常类型名称

### getExceptionMessage

> 获取异常详细信息。

- **Returns**: `String` - 异常详细信息
