# ChannelNotRegisterException
> 表示消息通道未注册的异常。
> <p>
> 当尝试在未注册的消息通道上发送或接收消息时，将抛出此异常。它包含未注册的通道名称，以便于调试和日志记录。
- **Type**: class
- **Package**: `com.euonia.bus.exception`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
| --- | --- | --- |
| `channel` | `String` | - |

## Methods

### super
- **Parameters**:
  - `registered."` (`String.format("Message channel '%s' is not`): -
  - `channel)` (``): -

### super
- **Parameters**:
  - `message` (``): -

### getChannel
> 获取未注册的消息通道名称。
- **Returns**: `String` — 未注册的消息通道名称

### ChannelNotRegisterException
> 构造一个新的 {@code ChannelNotRegisterException}，并指定未注册的通道名称。
- **Parameters**:
  - `channel` (`String`): 未注册的消息通道名称
- **Returns**: *(constructor)*

### ChannelNotRegisterException
> 构造一个新的 {@code ChannelNotRegisterException}，并指定未注册的通道名称和详细消息。
- **Parameters**:
  - `channel` (`String`): 未注册的消息通道名称
  - `message` (`String`): 详细的异常消息
- **Returns**: *(constructor)*