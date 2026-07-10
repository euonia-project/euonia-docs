# DefaultTransportStrategy
> 默认传输策略实现，默认拒绝所有发送和接收。
- **Type**: class
- **Package**: `com.euonia.bus.strategy`
- **Author**: (not specified)

## Methods
### getName
> 获取策略名称。
- **Returns**: `String` - "DefaultTransportStrategy"

### allowOutgoing
> 默认返回 `false`，拒绝所有发送。
- **Parameters**:
  - `channel` (`String`): 通道名
  - `messageType` (`Class<?>`): 消息类型
- **Returns**: `boolean` - 始终返回 `false`

### allowIncoming
> 默认返回 `false`，拒绝所有接收。
- **Parameters**:
  - `channel` (`String`): 通道名
  - `messageType` (`Class<?>`): 消息类型
- **Returns**: `boolean` - 始终返回 `false`
