# InboxHandle

> 收件箱（Inbox）消息的处理状态记录，跟踪每条消息被各处理器消费的执行状态。
> <p>
> 用于实现幂等消费，确保同一条消息不会被重复处理。
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

### `getHandler(): String`

**Returns:** `String` — 处理器的标识名称

### `setHandler(String handler): void`

**Parameters:**
- `handler` (`String`): 处理器的标识名称

### `getStatus(): int`

**Returns:** `int` — 处理状态（0=待处理, 1=成功, 2=失败）

### `setStatus(int status): void`

**Parameters:**
- `status` (`int`): 处理状态（0=待处理, 1=成功, 2=失败）

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

> 处理状态枚举。

#### `PENDING`

> 待处理

#### `SUCCESS`

> 处理成功

#### `FAILED`

> 处理失败

#### `getValue(): int`

> 获取状态对应的整数值。

**Returns:** `int` — 状态值
