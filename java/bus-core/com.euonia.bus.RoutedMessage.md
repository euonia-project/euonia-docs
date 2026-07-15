# RoutedMessage
> `RoutedMessage` 是表示带有路由信息的消息封装类。它实现了 `MessageEnvelope` 接口，为通过消息系统路由的消息提供公共属性和方法。
- **Type**: class
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `metadata` | `MessageMetadata` | 消息元数据容器 |
| `messageId` | `String` | 消息唯一标识符 |
| `correlationId` | `String` | 关联标识符，用于在请求-响应模式中关联消息 |
| `conversationId` | `String` | 会话标识符，用于关联同一对话中的多条消息 |
| `requestTrackId` | `String` | 请求追踪标识符，用于端到端请求追踪 |
| `channel` | `String` | 消息所属的通道名称 |
| `authorization` | `String` | 授权令牌 |
| `timestamp` | `long` | 消息时间戳（Unix 毫秒） |
| `payload` | `T` | 消息负载对象 |

## Methods
### RoutedMessage
> 创建一个空的路由消息实例。

### RoutedMessage
> 使用负载和通道创建路由消息，消息 ID 通过 `ObjectId` 自动生成。
- **Parameters**:
  - `payload` (`T`): 消息负载
  - `channel` (`String`): 消息通道

### RoutedMessage
> 使用负载、通道和消息 ID 创建路由消息。
- **Parameters**:
  - `payload` (`T`): 消息负载，不能为 null
  - `channel` (`String`): 消息通道
  - `messageId` (`String`): 消息唯一标识符

### getMessageId / setMessageId
> 获取/设置消息唯一标识符。

### getCorrelationId / setCorrelationId
> 获取/设置关联标识符。

### getConversationId / setConversationId
> 获取/设置会话标识符。

### getRequestTrackId / setRequestTrackId
> 获取/设置请求追踪标识符。

### getChannel / setChannel
> 获取/设置消息所属的通道名称。

### getAuthorization / setAuthorization
> 获取/设置授权令牌。

### getTimestamp / setTimestamp
> 获取/设置消息时间戳。

### getMetadata
> 获取消息元数据容器。
- **Returns**: `MessageMetadata` - 消息元数据

### getMetadata
> 根据键获取元数据值。
- **Parameters**:
  - `key` (`String`): 元数据键
- **Returns**: `Object` - 元数据值

### setMetadata
> 设置元数据键值对。
- **Parameters**:
  - `key` (`String`): 元数据键
  - `value` (`Object`): 元数据值

### getMetadata
> 根据键和类型获取元数据值。
- **Parameters**:
  - `key` (`String`): 元数据键
  - `type` (`Class<V>`): 值的类型
- **Returns**: `V` - 元数据值

### getPayload
> 获取消息负载。
- **Returns**: `T` - 消息负载

### setPayload
> 设置消息负载，并自动将负载类名写入类型名称元数据。
- **Parameters**:
  - `payload` (`T`): 消息负载

### getTypeName / setTypeName
> 获取/设置消息类型名称（负载类的完全限定名）。

### toString
> 返回消息的字符串表示，格式为 `messageId:{typeName}`。
- **Returns**: `String` - 字符串表示
