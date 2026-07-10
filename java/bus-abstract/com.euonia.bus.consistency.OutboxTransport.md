# OutboxTransport
> 发件箱消息的传输状态记录，跟踪每条消息在各个传输通道上的发送状态。
> <p>
> 包含传输名称、发送状态（待发送/成功/失败）、重试次数和错误信息。
> 状态由内部枚举 {@link Status} 定义。
- **Type**: class
- **Package**: `com.euonia.bus.consistency`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
| --- | --- | --- |
| `messageId` | `String` | 关联的消息 ID |
| `transport` | `String` | 传输名称 |
| `status` | `int` | 发送状态（0=待发送, 1=成功, 2=失败） |
| `retryAttempts` | `int` | 已重试次数 |
| `error` | `String` | 最近一次错误信息 |
| `value` | `int` | - |

## Methods

### getMessageId
- **Returns**: `String` — -

### setMessageId
- **Parameters**:
  - `messageId` (`String`): -

### getTransport
- **Returns**: `String` — -

### setTransport
- **Parameters**:
  - `transport` (`String`): -

### getStatus
- **Returns**: `int` — -

### setStatus
- **Parameters**:
  - `status` (`int`): -

### getRetryAttempts
- **Returns**: `int` — -

### setRetryAttempts
- **Parameters**:
  - `retryAttempts` (`int`): -

### getError
- **Returns**: `String` — -

### setError
- **Parameters**:
  - `error` (`String`): -

### PENDING
> 待发送
- **Parameters**:
  - `0` (``): -

### Status
- **Parameters**:
  - `value` (`int`): -

### getValue
> 获取状态对应的整数值。
- **Returns**: `int` — 状态值