# DefaultConfigurator
> DefaultConfigurator 是 `Configurator` 接口的默认实现。它提供了用于配置消息约定、传输策略和处理器注册的流式 API。
- **Type**: class
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Methods
### getDefaultTransport
> 获取默认传输方式。
- **Returns**: `String` - 默认传输名称

### isEnablePipelineBehaviors
> 检查是否启用管道行为。
- **Returns**: `boolean` - 启用状态

### getConventionBuilder
> 获取消息约定构建器。
- **Returns**: `MessageConventionBuilder` - 消息约定构建器

### getStrategyBuilders
> 获取传输策略构建器映射。
- **Returns**: `ConcurrentMap<String, TransportStrategyBuilder>` - 传输策略构建器映射

### getRegistrations
> 获取已注册的处理器列表。
- **Returns**: `Map<String, ChannelRegistration>` - 已注册的处理器列表

### setConvention
> 配置消息约定。
- **Parameters**:
  - `conventionConfig` (`Consumer<MessageConventionBuilder>`): 消息约定配置
- **Returns**: `DefaultConfigurator` - 当前配置器实例

### setStrategy
> 配置传输策略。
- **Parameters**:
  - `name` (`String`): 策略名称
  - `strategyConfig` (`Consumer<TransportStrategyBuilder>`): 策略配置
- **Returns**: `DefaultConfigurator` - 当前配置器实例

### registerChannel
> 注册处理器（Lambda 函数形式）。
- **Parameters**:
  - `channel` (`String`): 通道名称
  - `messageType` (`Class<T>`): 消息类型
  - `handler` (`BiFunction<T, MessageContext, R>`): 处理器函数
- **Returns**: `DefaultConfigurator` - 当前配置器实例

### registerChannel
> 注册处理器（ChannelHandler 形式）。
- **Parameters**:
  - `channel` (`String`): 通道名称
  - `messageType` (`Class<?>`): 消息类型
  - `handler` (`ChannelHandler`): 处理器处理信息
- **Returns**: `DefaultConfigurator` - 当前配置器实例

### registerChannel
> 注册处理器（ChannelHandler 列表形式）。
- **Parameters**:
  - `channel` (`String`): 通道名称
  - `messageType` (`Class<?>`): 消息类型
  - `handling` (`List<ChannelHandler>`): 处理器处理信息列表
- **Returns**: `DefaultConfigurator` - 当前配置器实例

### registerChannel
> 注册处理器（类型列表形式）。
- **Parameters**:
  - `types` (`List<Class<?>>`): 处理器类型列表
- **Returns**: `DefaultConfigurator` - 当前配置器实例

### registerChannel
> 注册处理器（类型数组形式）。
- **Parameters**:
  - `types` (`Class<?>...`): 处理器类型数组
- **Returns**: `DefaultConfigurator` - 当前配置器实例

### registerChannel
> 注册处理器（包名形式）。
- **Parameters**:
  - `packageNames` (`String...`): 包名数组
- **Returns**: `DefaultConfigurator` - 当前配置器实例

### setDefaultTransport
> 设置默认传输方式。
- **Parameters**:
  - `defaultTransportSupplier` (`Supplier<String>`): 默认传输方式的提供者
- **Returns**: `DefaultConfigurator` - 当前配置器实例

### setEnablePipelineBehaviors
> 设置是否启用管道行为。
- **Parameters**:
  - `enablePipelineBehaviorsSupplier` (`Supplier<Boolean>`): 启用管道行为的提供者
- **Returns**: `DefaultConfigurator` - 当前配置器实例
