# OutboxEntry
> 代表收件箱（Outbox）中待发送的持久化消息。
> <p>
> 业务事务中将领域事件写入 {@link OutboxStore}，由 {@code OutboxPublisher}
> 异地轮询并以至少一次的方式投递到消息总线。
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
| `transports` | `List<OutboxTransport>` | 关联的传输状态列表 |

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

### getTransports
- **Returns**: `List<OutboxTransport>` — -

### setTransports
- **Parameters**:
  - `transports` (`List<OutboxTransport>`): -

### addTransport
> 添加一条传输状态记录。
- **Parameters**:
  - `transport` (`OutboxTransport`): 传输状态

### addTransports
> 按传输名称添加传输记录（当前为空实现）。
- **Parameters**:
  - `transport` (`String`): 传输名称

### toString
> 返回投递箱条目的字符串表示。
- **Returns**: `String` — 格式为 {@code OutboxMessage{messageId=xxx, channel=xxx}} 的字符串