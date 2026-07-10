# HandlerDelegate
> 处理器委托函数式接口，定义处理消息并返回结果的契约。该接口作为 `HandlerFactory` 创建的委托的实际执行入口，由框架内部使用，不应由应用程序直接实现。
- **Type**: interface
- **Package**: `com.euonia.bus.handle`
- **Author**: damon(zhaorong@outlook.com)

## Methods
### handle
> 处理给定的消息并返回结果。
- **Parameters**:
  - `message` (`Object`): 要处理的消息对象
  - `context` (`MessageContext`): 消息处理上下文
- **Returns**: `Object` - 处理结果，可以为 `null`
