# ChannelRegistrar
> ChannelRegistrar 是一个用于注册和管理通道处理器的类。它提供了注册通道处理器、获取已注册的通道处理器列表以及获取指定通道的注册信息的方法。该类使用单例模式，确保在整个应用程序中只有一个实例。
- **Type**: class
- **Package**: `com.euonia.bus`
- **Author**: (not specified)

## Methods
### instance
> 获取 ChannelRegistrar 的单例实例。
- **Returns**: `ChannelRegistrar` - ChannelRegistrar 的单例实例

### getRegistrations
> 获取已注册的通道处理器列表。
- **Returns**: `Map<String, ChannelRegistration>` - 已注册的通道处理器列表

### getRegistration
> 获取指定通道的注册信息。
- **Parameters**:
  - `channel` (`String`): 通道名称
- **Returns**: `Optional<ChannelRegistration>` - 指定通道的注册信息，如果不存在则返回空的 Optional

### register
> 注册一个通道处理器。
- **Parameters**:
  - `channel` (`String`): 通道名称
  - `messageType` (`Class<?>`): 消息类型
  - `handler` (`ChannelHandler`): 通道处理器
- **Returns**: `ChannelRegistrar` - ChannelRegistrar 实例

### register
> 注册一个通道处理器列表。
- **Parameters**:
  - `channel` (`String`): 通道名称
  - `messageType` (`Class<?>`): 消息类型
  - `handling` (`List<ChannelHandler>`): 通道处理器列表
- **Returns**: `ChannelRegistrar` - ChannelRegistrar 实例

### registrar
> 注册通道。
- **Parameters**:
  - `types` (`List<Class<?>>`): 处理器类型列表
- **Returns**: `ChannelRegistrar` - ChannelRegistrar 实例

### registrar
> 注册通道。
- **Parameters**:
  - `types` (`Class<?>...`): 处理器类型数组
- **Returns**: `ChannelRegistrar` - ChannelRegistrar 实例

### registrar
> 注册通道。
- **Parameters**:
  - `packageNames` (`String...`): 包名数组
- **Returns**: `ChannelRegistrar` - ChannelRegistrar 实例

### register
> 注册一个通道处理器（Lambda 表达式形式）。
- **Parameters**:
  - `channel` (`String`): 通道名称
  - `messageType` (`Class<T>`): 消息类型
  - `handler` (`BiFunction<T, MessageContext, R>`): 通道处理器
- **Returns**: `ChannelRegistrar` - ChannelRegistrar 实例
