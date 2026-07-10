# MessageRepliedEvent
> 消息已回复事件，包含回复的结果。
- **Type**: class
- **Package**: `com.euonia.bus.event`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
| --- | --- | --- |
| `result` | `Object` | 回复结果 |

## Methods

### super
- **Parameters**:
  - `message` (``): -
  - `null` (``): -
  - `MessageProcessType.REPLIED` (``): -

### getResult
> 获取回复的结果。
- **Returns**: `Object` — 回复的结果

### MessageRepliedEvent
> 使用消息和回复结果构造消息已回复事件。
- **Parameters**:
  - `message` (`Object`): 原始消息
  - `result` (`Object`): 回复的结果
- **Returns**: *(constructor)*