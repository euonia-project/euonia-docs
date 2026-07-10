# OverridableTransportStrategy
> (package-private) 包装内部策略的可覆盖传输策略，允许通过谓词覆盖 `allowOutgoing` 和 `allowIncoming` 的判断逻辑。
- **Type**: class
- **Package**: `com.euonia.bus.strategy`
- **Author**: (not specified)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `delegate` | `TransportStrategy` | 内部委托策略 |
| `outgoingPredicate` | `BiPredicate<String, Class<?>>` | 发送谓词覆盖 |
| `incomingPredicate` | `BiPredicate<String, Class<?>>` | 接收谓词覆盖 |

## Methods
### OverridableTransportStrategy
> 构造方法。
- **Parameters**:
  - `delegate` (`TransportStrategy`): 内部委托策略

### getName
> 获取策略名称。
- **Returns**: `String` - 格式为 "Override with ({委托策略名})"

### allowOutgoing
> 判断是否允许发送。如果设置了自定义谓词则使用自定义逻辑，否则委托给内部策略。
- **Parameters**:
  - `channel` (`String`): 通道名
  - `messageType` (`Class<?>`): 消息类型
- **Returns**: `boolean` - 是否允许

### allowIncoming
> 判断是否允许接收。如果设置了自定义谓词则使用自定义逻辑，否则委托给内部策略。
- **Parameters**:
  - `channel` (`String`): 通道名
  - `messageType` (`Class<?>`): 消息类型
- **Returns**: `boolean` - 是否允许

### setOutgoingPredicate / setIncomingPredicate
> 设置对应的谓词覆盖。
