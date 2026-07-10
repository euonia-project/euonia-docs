# MessageProcessedEvent
> 消息处理事件的基类，封装消息处理过程中的通用状态。
- **Type**: class
- **Package**: `com.euonia.bus.event`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
| --- | --- | --- |
| `message` | `Object` | 处理的消息 |
| `context` | `MessageContext` | 消息处理上下文 |
| `processType` | `MessageProcessType` | 处理类型 |

## Methods

### getMessage
> 获取处理的消息。
- **Returns**: `Object` — 消息对象

### getContext
> 获取消息处理上下文。
- **Returns**: `MessageContext` — 处理上下文

### getProcessType
> 获取处理类型。
- **Returns**: `MessageProcessType` — 处理类型

### MessageProcessedEvent
> 使用消息、上下文和处理类型构造事件。
- **Parameters**:
  - `message` (`Object`): 处理的消息
  - `context` (`MessageContext`): 消息处理上下文
  - `processType` (`MessageProcessType`): 处理类型
- **Returns**: *(constructor)*