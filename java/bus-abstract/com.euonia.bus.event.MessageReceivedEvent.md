# MessageReceivedEvent
> 消息接收事件，表示消息已被接收但尚未处理完成。
- **Type**: class
- **Package**: `com.euonia.bus.event`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### super
- **Parameters**:
  - `message` (``): -
  - `context` (``): -
  - `MessageProcessType.RECEIVED` (``): -

### MessageReceivedEvent
> 使用消息和处理上下文构造消息接收事件。
- **Parameters**:
  - `message` (`Object`): 已接收的消息
  - `context` (`MessageContext`): 处理上下文
- **Returns**: *(constructor)*