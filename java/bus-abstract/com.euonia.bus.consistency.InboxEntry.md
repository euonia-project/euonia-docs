# InboxEntry

> 收件箱（Inbox）条目，用于幂等处理。

- **Type**: class
- **Package**: `com.euonia.bus.consistency`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### `getMessageId(): String`

**Returns:** `String` — 消息唯一标识符

### `setMessageId(String messageId): void`

**Parameters:**
- `messageId` (`String`): 消息唯一标识符

### `getChannel(): String`

**Returns:** `String` — 消息所属通道

### `setChannel(String channel): void`

**Parameters:**
- `channel` (`String`): 消息所属通道

### `getMessageType(): String`

**Returns:** `String` — 消息类型名称

### `setMessageType(String messageType): void`

**Parameters:**
- `messageType` (`String`): 消息类型名称

### `getContent(): MessageEnvelope<?>`

**Returns:** `MessageEnvelope<?>` — 消息内容（负载）

### `setContent(MessageEnvelope<?> content): void`

**Parameters:**
- `content` (`MessageEnvelope<?>`): 消息内容（负载）

### `getCreatedAt(): LocalDateTime`

**Returns:** `LocalDateTime` — 条目创建时间

### `setCreatedAt(LocalDateTime createdAt): void`

**Parameters:**
- `createdAt` (`LocalDateTime`): 条目创建时间

### `getHandles(): List<InboxHandle>`

**Returns:** `List<InboxHandle>` — 处理状态列表

### `setHandles(List<InboxHandle> handles): void`

**Parameters:**
- `handles` (`List<InboxHandle>`): 处理状态列表

### `addHandle(InboxHandle handle): void`

> 添加一条处理状态记录。

**Parameters:**
- `handle` (`InboxHandle`): 处理状态

### `addHandle(String handler): void`

> 为指定处理器创建并添加一条待处理状态记录。

**Parameters:**
- `handler` (`String`): 处理器名称

### `toString(): String`

> 返回收件箱条目的字符串表示。

**Returns:** `String` — 格式为 `InboxEntry{channel=xxx, messageId=xxx, messageType=xxx}` 的字符串
