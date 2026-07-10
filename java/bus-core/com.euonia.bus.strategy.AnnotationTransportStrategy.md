# AnnotationTransportStrategy
> 基于 `@DispatchIn` 和 `@ReceiveIn` 注解判断消息传输策略。检查消息类型上的注解包含的传输名称是否与构造时指定的 `required` 传输匹配。
- **Type**: class
- **Package**: `com.euonia.bus.strategy`
- **Author**: (not specified)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `required` | `String[]` | 需要的传输名称 |

## Methods
### AnnotationTransportStrategy
> 构造方法。
- **Parameters**:
  - `required` (`String...`): 需要的传输名称

### getName
> 获取策略名称。
- **Returns**: `String` - "AnnotationTransportStrategy"

### allowOutgoing
> 通过检查消息类型上的 `@DispatchIn` 注解判断是否允许发送。
- **Parameters**:
  - `channel` (`String`): 通道名
  - `messageType` (`Class<?>`): 消息类型
- **Returns**: `boolean` - 是否允许

### allowIncoming
> 通过检查消息类型上的 `@ReceiveIn` 注解判断是否允许接收。
- **Parameters**:
  - `channel` (`String`): 通道名
  - `messageType` (`Class<?>`): 消息类型
- **Returns**: `boolean` - 是否允许
