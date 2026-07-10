# InboxEntry
> 收件箱（Inbox）条目，用于幂等处理。
- **Type**: class
- **Package**: `com.euonia.bus.consistency`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
| --- | --- | --- |
| `messageId` | `String` | 消息唯一标识符 |
| `channel` | `String` | 消息所属通道 |
| `messageType` | `String` | 消息类型名称 |
| `createdAt` | `LocalDateTime` | 条目创建时间 |
| `handles` | `List<InboxHandle>` | 处理状态列表 |

## Methods

### getMessageId
- **Returns**: `String` — -

### setMessageId
- **Parameters**:
  - `messageId` (`String`): -

### getChannel
- **Returns**: `String` — -

### setChannel
- **Parameters**:
  - `channel` (`String`): -

### getMessageType
- **Returns**: `String` — -

### setMessageType
- **Parameters**:
  - `messageType` (`String`): -

### getContent
- **Returns**: `>` — -

### setContent
- **Parameters**:
  - `content` (`MessageEnvelope<?>`): -

### getCreatedAt
- **Returns**: `LocalDateTime` — -

### setCreatedAt
- **Parameters**:
  - `createdAt` (`LocalDateTime`): -

### getHandles
- **Returns**: `List<InboxHandle>` — -

### setHandles
- **Parameters**:
  - `handles` (`List<InboxHandle>`): -

### addHandle
> 添加一条处理状态记录。
- **Parameters**:
  - `handle` (`InboxHandle`): 处理状态

### addHandle
> 为指定处理器创建并添加一条待处理状态记录。
- **Parameters**:
  - `handler` (`String`): 处理器名称

### toString
> 返回收件箱条目的字符串表示。
- **Returns**: `String` — 格式为 {@code InboxEntry{channel=xxx, messageId=xxx, messageType=xxx}} 的字符串