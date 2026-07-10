# AnnotationMessageConvention
> Evaluate whether a type is a message, command, event, or request by annotation decorated on the type.
- **Type**: class
- **Package**: `com.euonia.bus.convention`
- **Author**: (not specified)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `NAME` | `String` | 约定名称："Annotation decoration message convention" |

## Methods
### getName
> 获取约定名称。
- **Returns**: `String` - "Annotation decoration message convention"

### isUnicast
> 通过通道注册信息中消息类型上的 `@Unicast` 注解判断是否为单播消息。
- **Parameters**:
  - `channel` (`String`): 通道名
- **Returns**: `boolean` - 是否为单播消息

### isMulticast
> 通过通道注册信息中消息类型上的 `@Multicast` 注解判断是否为组播消息。
- **Parameters**:
  - `channel` (`String`): 通道名
- **Returns**: `boolean` - 是否为组播消息

### isRequest
> 通过通道注册信息中消息类型上的 `@Request` 注解判断是否为请求消息。
- **Parameters**:
  - `channel` (`String`): 通道名
- **Returns**: `boolean` - 是否为请求消息
