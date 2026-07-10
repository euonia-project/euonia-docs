# MessageDeliveredEvent
> 消息已投递事件，表示消息已成功投递到目标传输。
- **Type**: class
- **Package**: `com.euonia.bus.event`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### super
- **Parameters**:
  - `message` (``): -
  - `context` (``): -
  - `MessageProcessType.DELIVERED` (``): -

### MessageDeliveredEvent
> 使用消息和处理上下文构造消息已投递事件。
- **Parameters**:
  - `message` (`Object`): 已投递的消息
  - `context` (`MessageContext`): 处理上下文
- **Returns**: *(constructor)*