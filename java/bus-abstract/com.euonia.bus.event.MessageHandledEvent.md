# MessageHandledEvent
> 消息已处理事件，表示消息已被处理器处理完成。
- **Type**: class
- **Package**: `com.euonia.bus.event`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
| --- | --- | --- |
| `message` | `Object` | 已处理的消息 |

## Methods

### super
- **Parameters**:
  - `message` (``): -
  - `null` (``): -
  - `MessageProcessType.HANDLED` (``): -

### getHandlerType
- **Returns**: `>` — -

### setHandlerType
> 设置处理该消息的处理器类型。
- **Parameters**:
  - `handlerType` (`Class<?>`): 处理器类型

### getMessage
> 返回已处理的消息。
- **Returns**: `Object` — 消息对象

### MessageHandledEvent
> 使用已处理的消息构造事件。
- **Parameters**:
  - `message` (`Object`): 已处理的消息
- **Returns**: *(constructor)*