# OutboxTransport

> 发件箱消息的传输状态记录，跟踪每条消息在各个传输通道上的发送状态。
> <p>
> 包含传输名称、发送状态（待发送/成功/失败）、重试次数和错误信息。
> 状态由内部枚举 `Status` 定义。

- **Type**: class
- **Package**: `com.euonia.bus.consistency`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### `getMessageId(): String`

**Returns:** `String` — 关联的消息 ID

### `setMessageId(String messageId): void`

**Parameters:**
- `messageId` (`String`): 关联的消息 ID

### `getTransport(): String`

**Returns:** `String` — 传输名称

### `setTransport(String transport): void`

**Parameters:**
- `transport` (`String`): 传输名称

### `getStatus(): int`

**Returns:** `int` — 发送状态（0=待发送, 1=成功, 2=失败）

### `setStatus(int status): void`

**Parameters:**
- `status` (`int`): 发送状态（0=待发送, 1=成功, 2=失败）

### `getRetryAttempts(): int`

**Returns:** `int` — 已重试次数

### `setRetryAttempts(int retryAttempts): void`

**Parameters:**
- `retryAttempts` (`int`): 已重试次数

### `getError(): String`

**Returns:** `String` — 最近一次错误信息

### `setError(String error): void`

**Parameters:**
- `error` (`String`): 最近一次错误信息

## Inner Types

### `Status` (enum)

> 传输状态枚举。

#### `PENDING`

> 待发送

#### `SUCCESS`

> 发送成功

#### `FAILED`

> 发送失败

#### `getValue(): int`

> 获取状态对应的整数值。

**Returns:** `int` — 状态值
