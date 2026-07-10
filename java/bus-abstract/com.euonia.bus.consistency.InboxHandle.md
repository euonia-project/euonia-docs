# InboxHandle
> 收件箱（Inbox）消息的处理状态记录，跟踪每条消息被各处理器消费的执行状态。
> <p>
> 用于实现幂等消费，确保同一条消息不会被重复处理。
> 状态由内部枚举 {@link Status} 定义。
- **Type**: class
- **Package**: `com.euonia.bus.consistency`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
| --- | --- | --- |
| `messageId` | `String` | 关联的消息 ID |
| `handler` | `String` | 处理器的标识名称 |
| `status` | `int` | 处理状态（0=待处理, 1=成功, 2=失败） |
| `retryAttempts` | `int` | 已重试次数 |
| `error` | `String` | 最近一次错误信息 |
| `value` | `int` | - |

## Methods

### getMessageId
- **Returns**: `String` — -

### setMessageId
- **Parameters**:
  - `messageId` (`String`): -

### getHandler
- **Returns**: `String` — -

### setHandler
- **Parameters**:
  - `handler` (`String`): -

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
> 待处理
- **Parameters**:
  - `0` (``): -

### Status
- **Parameters**:
  - `value` (`int`): -

### getValue
> 获取状态对应的整数值。
- **Returns**: `int` — 状态值