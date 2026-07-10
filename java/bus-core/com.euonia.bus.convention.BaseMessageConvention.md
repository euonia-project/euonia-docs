# BaseMessageConvention
> 内置的消息约定，聚合多个 `MessageConvention` 实例，并使用 `ConcurrentHashMap` 缓存类型分类结果。每种消息类型（unicast、multicast、request）都有自己专用的缓存。
- **Type**: class
- **Package**: `com.euonia.bus.convention`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `defaultConvention` | `OverridableMessageConvention` | 默认可覆盖的消息约定实例 |
| `conventions` | `List<MessageConvention>` | 已注册的消息约定列表 |
| `unicastConventionCache` | `ConventionCache` | 单播消息类型判断的缓存 |
| `multicastConventionCache` | `ConventionCache` | 组播消息类型判断的缓存 |
| `requestConventionCache` | `ConventionCache` | 请求消息类型判断的缓存 |

## Methods
### BaseMessageConvention
> 构造方法，初始化时注册默认可覆盖的约定。

### isUnicast
> 判断指定的通道是否为单播消息类型。
- **Parameters**:
  - `channel` (`String`): 待检查的通道，不能为 `null`
- **Returns**: `boolean` - 若任一已注册的约定将该类型归类为单播，返回 `true`

### isMulticast
> 判断指定的通道是否为组播消息类型。
- **Parameters**:
  - `channel` (`String`): 待检查的通道，不能为 `null`
- **Returns**: `boolean` - 若任一已注册的约定将该类型归类为组播，返回 `true`

### isRequest
> 判断指定的通道是否为请求消息类型。
- **Parameters**:
  - `channel` (`String`): 待检查的通道，不能为 `null`
- **Returns**: `boolean` - 若任一已注册的约定将该类型归类为请求，返回 `true`

### getName
> 获取此约定的名称。
- **Returns**: `String` - 约定的名称，始终为 "Default"

### defineUnicastTypeConvention
> 定义单播类型的判断条件。
- **Parameters**:
  - `convention` (`Predicate<String>`): 判断指定类型是否为单播的谓词

### defineMulticastTypeConvention
> 定义组播类型的判断条件。
- **Parameters**:
  - `convention` (`Predicate<String>`): 判断指定类型是否为组播的谓词

### defineRequestTypeConvention
> 定义请求类型的判断条件。
- **Parameters**:
  - `convention` (`Predicate<String>`): 判断指定类型是否为请求的谓词

### defineTypeConvention
> 定义统一的类型约定，将消息类型映射到其 `MessageConventionType`。
- **Parameters**:
  - `convention` (`Function<String, MessageConventionType>`): 将类型分类为约定类别的函数

### add
> 添加一个或多个额外的消息约定。
- **Parameters**:
  - `conventions` (`MessageConvention...`): 要添加的约定数组

### getRegisteredConventions
> 返回所有已注册约定的名称（用于诊断目的）。
- **Returns**: `String[]` - 已注册约定的名称数组
