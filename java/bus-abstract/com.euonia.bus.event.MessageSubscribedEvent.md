# MessageSubscribedEvent
> 消息订阅事件，表示一个新处理器被订阅到某个消息通道。
> 包含通道名称、消息类型和处理器类型。
- **Type**: class
- **Package**: `com.euonia.bus.event`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
| --- | --- | --- |
| `channel` | `String` | 订阅的通道名称 |

## Methods

### getChannel
> 获取订阅的通道名称。
- **Returns**: `String` — 通道名称

### getMessageType
- **Returns**: `>` — -

### getHandlerType
- **Returns**: `>` — -

### MessageSubscribedEvent
> 使用通道名、消息类型和处理器类型构造消息订阅事件。
- **Parameters**:
  - `channel` (`String`): 通道名称
  - `messageType` (`Class<?>`): 消息类型
  - `handlerType` (`Class<?>`): 处理器类型
- **Returns**: *(constructor)*