# Configurator
> {@link Configurator} 是配置消息总线的主接口。
> 提供了配置消息约定、传输策略和处理器注册的方法。
> 此接口的实现将在总线启动之前用于设置总线。
- **Type**: interface
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### getDefaultTransport
> 获取默认传输策略名称，可用于消息路由和分类。
- **Returns**: `String` — 默认传输策略名称

### isEnablePipelineBehaviors
> 获取是否启用管道行为，可用于消息处理和操作。
- **Returns**: `boolean` — 如果管道行为已启用则返回 true，否则返回 false

### getConventionBuilder
> 获取已配置的 {@link MessageConventionBuilder}。
- **Returns**: `MessageConventionBuilder` — MessageConventionBuilder 实例

### getStrategyBuilders
> 获取已配置的传输策略构建器映射。
- **Returns**: `ConcurrentMap<String, TransportStrategyBuilder>` — 传输策略构建器映射

### getRegistrations
> 获取已配置的处理器注册信息映射。
- **Returns**: `Map<String, ChannelRegistration>` — 处理器注册信息映射

### getConvention
> 获取消息约定，可用于消息格式化和验证。
- **Returns**: `MessageConvention` — 消息约定

### getStrategyAssignedTypes
> 获取传输策略名称列表，可用于消息路由和分类。
- **Returns**: `List<String>` — 传输策略名称列表

### getStrategy
> 获取指定传输名称对应的传输策略，可用于消息路由和分类。
- **Parameters**:
  - `transport` (`String`): 传输名称
- **Returns**: `TransportStrategy` — 指定传输名称对应的传输策略，如果未找到则返回 null