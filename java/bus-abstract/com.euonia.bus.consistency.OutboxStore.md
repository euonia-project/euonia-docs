# OutboxStore

> 发件箱（Outbox）持久化接口，保证领域事件与业务数据在同一事务中写入。

- **Type**: interface
- **Package**: `com.euonia.bus.consistency`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### `insert(MessageEnvelope<?> message, List<String> transports): boolean`

> 插入一条消息到发件箱。

**Parameters:**
- `message` (`MessageEnvelope<?>`): 消息内容
- `transports` (`List<String>`): 投递方式列表

**Returns:** `boolean` — 插入是否成功

### `insert(OutboxEntry entry): boolean`

> 插入一条消息到发件箱。

**Parameters:**
- `entry` (`OutboxEntry`): 消息条目

**Returns:** `boolean` — 插入是否成功

### `markAsSuccess(String messageId, String transport): void`

> 标记消息投递成功。

**Parameters:**
- `messageId` (`String`): 消息ID
- `transport` (`String`): 投递方式

### `markAsFailed(String messageId, String transport, String errorMessage): void`

> 标记消息投递失败。

**Parameters:**
- `messageId` (`String`): 消息ID
- `transport` (`String`): 投递方式
- `errorMessage` (`String`): 错误信息

### `get(String messageId): OutboxEntry`

> 获取发件箱条目。

**Parameters:**
- `messageId` (`String`): 消息ID

**Returns:** `OutboxEntry` — 发件箱条目

### `getAndCache(String messageId): OutboxEntry`

> 获取发件箱条目并缓存。

**Parameters:**
- `messageId` (`String`): 消息ID

**Returns:** `OutboxEntry` — 发件箱条目

### `clearCache(): void`

> 清除缓存。

### `getFailedMessages(): List<OutboxTransport>`

> 获取投递失败的消息列表。

**Returns:** `List<OutboxTransport>` — 投递失败的消息列表
