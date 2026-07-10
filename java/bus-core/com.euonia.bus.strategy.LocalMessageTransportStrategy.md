# LocalMessageTransportStrategy
> 基于 `@LocalMessage` 注解的传输策略。消息类型带有该注解时允许发送和接收。
- **Type**: class
- **Package**: `com.euonia.bus.strategy`
- **Author**: (not specified)

## Methods
### getName
> 获取策略名称。
- **Returns**: `String` - "LocalMessageTransportStrategy"

### allowOutgoing
> 通过检查消息类型上是否有 `@LocalMessage` 注解判断是否允许发送。
- **Parameters**:
  - `channel` (`String`): 通道名
  - `messageType` (`Class<?>`): 消息类型
- **Returns**: `boolean` - 是否允许

### allowIncoming
> 通过检查消息类型上是否有 `@LocalMessage` 注解判断是否允许接收。
- **Parameters**:
  - `channel` (`String`): 通道名
  - `messageType` (`Class<?>`): 消息类型
- **Returns**: `boolean` - 是否允许
