# MessageEnvelope

> `MessageEnvelope` 定义了通过总线发送的消息的元数据接口。
>
> 提供消息路由和追踪所需的核心标识信息，包括消息 ID、关联 ID、
> 会话 ID、请求追踪 ID 和通道名称。

- **Type**: interface
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<T>` — 消息负载类型

## Methods

### `getMessageId(): String`

> 获取消息唯一标识符。

**Returns:** `String` — 消息 ID

### `getCorrelationId(): String`

> 获取关联标识符，用于在请求-响应模式中关联消息。

**Returns:** `String` — 关联 ID

### `getConversationId(): String`

> 获取会话标识符，用于关联同一对话中的多条消息。

**Returns:** `String` — 会话 ID

### `getRequestTrackId(): String`

> 获取请求追踪标识符，用于端到端请求追踪。

**Returns:** `String` — 请求追踪 ID

### `getChannel(): String`

> 获取消息所属的通道名称。

**Returns:** `String` — 通道名称

### `getAuthorization(): String`

> 获取消息的授权令牌，用于验证消息发送者的身份和权限。

**Returns:** `String` — 授权令牌

### `getTimestamp(): long`

> 获取消息的时间戳，表示消息创建的时间，通常以 Unix 毫秒表示。

**Returns:** `long` — 消息时间戳

### `getPayload(): T`

> 获取消息负载对象。

**Returns:** `T` — 消息负载

### `getTypeName(): String`

> 获取消息类型名称，通常用于在消息系统中标识消息的类型。

**Returns:** `String` — 消息类型名称

### `getMetadata(): MessageMetadata`

> 获取消息的元数据对象，包含消息的附加信息和属性。

**Returns:** `MessageMetadata` — 消息元数据
