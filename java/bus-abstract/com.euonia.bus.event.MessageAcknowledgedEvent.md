# MessageAcknowledgedEvent
> 消息确认事件，表示消息处理已完成并已确认。
- **Type**: class
- **Package**: `com.euonia.bus.event`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### super
- **Parameters**:
  - `message` (``): -
  - `context` (``): -
  - `MessageProcessType.RECEIVED` (``): -

### MessageAcknowledgedEvent
> 使用消息和处理上下文构造消息确认事件。
- **Parameters**:
  - `message` (`Object`): 已确认的消息
  - `context` (`MessageContext`): 处理上下文
- **Returns**: *(constructor)*