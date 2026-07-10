# HandlerFactory
> 处理器委托工厂的函数式接口，用于通过 `ServiceProvider` 创建 `HandlerDelegate` 实例。
- **Type**: interface
- **Package**: `com.euonia.bus.handle`
- **Author**: damon(zhaorong@outlook.com)

## Methods
### createDelegate
> 创建一个新的 `HandlerDelegate` 实例。
- **Parameters**:
  - `provider` (`ServiceProvider`): 用于解析依赖的服务提供者
- **Returns**: `HandlerDelegate` - 一个新的 HandlerDelegate 实例
