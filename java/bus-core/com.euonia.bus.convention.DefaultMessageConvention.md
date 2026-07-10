# DefaultMessageConvention
> DefaultMessageConvention is a simple implementation of the MessageConvention interface that uses class type checks to determine the message type. It considers any class that implements `Unicast` as a unicast message, any class that implements `Multicast` as a multicast message, and any class that implements `Request` as a request message.
- **Type**: class
- **Package**: `com.euonia.bus.convention`
- **Author**: (not specified)

## Methods
### getName
> 获取约定名称。
- **Returns**: `String` - 类名

### isUnicast
> 通过检查消息类型是否实现了 `Unicast` 接口判断是否为单播消息。
- **Parameters**:
  - `channel` (`String`): 通道名
- **Returns**: `boolean` - 是否为单播消息

### isMulticast
> 通过检查消息类型是否实现了 `Multicast` 接口判断是否为组播消息。
- **Parameters**:
  - `channel` (`String`): 通道名
- **Returns**: `boolean` - 是否为组播消息

### isRequest
> 通过检查消息类型是否实现了 `Request` 接口判断是否为请求消息。
- **Parameters**:
  - `channel` (`String`): 通道名
- **Returns**: `boolean` - 是否为请求消息
