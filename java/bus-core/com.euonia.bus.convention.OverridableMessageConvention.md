# OverridableMessageConvention
> (package-private) 包装内部约定的可覆盖消息约定，允许通过谓词覆盖 `isUnicast`、`isMulticast`、`isRequest` 的判断逻辑。
- **Type**: class
- **Package**: `com.euonia.bus.convention`
- **Author**: (not specified)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `innerConvention` | `MessageConvention` | 内部约定 |
| `unicastPredicate` | `Predicate<String>` | 单播谓词覆盖 |
| `multicastPredicate` | `Predicate<String>` | 组播谓词覆盖 |
| `requestPredicate` | `Predicate<String>` | 请求谓词覆盖 |

## Methods
### OverridableMessageConvention
> 构造方法。
- **Parameters**:
  - `innerConvention` (`MessageConvention`): 内部约定

### getName
> 获取约定名称。
- **Returns**: `String` - 格式为 "Override with {内部约定名}"

### isUnicast
> 判断是否为单播消息。如果设置了自定义谓词则使用自定义逻辑，否则委托给内部约定。
- **Parameters**:
  - `channel` (`String`): 通道名
- **Returns**: `boolean` - 是否为单播消息

### isMulticast
> 判断是否为组播消息。如果设置了自定义谓词则使用自定义逻辑，否则委托给内部约定。
- **Parameters**:
  - `channel` (`String`): 通道名
- **Returns**: `boolean` - 是否为组播消息

### isRequest
> 判断是否为请求消息。如果设置了自定义谓词则使用自定义逻辑，否则委托给内部约定。
- **Parameters**:
  - `channel` (`String`): 通道名
- **Returns**: `boolean` - 是否为请求消息

### setUnicastPredicate / setMulticastPredicate / setRequestPredicate
> 设置对应的谓词覆盖。
