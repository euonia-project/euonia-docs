# MessageBus
> 消息总线的默认实现，实现 `Bus` 接口。`MessageBus` 是 Euonia 消息系统的核心组件，负责协调消息的发布、发送和请求-响应调用。它利用 `Dispatcher` 确定消息应路由到哪些传输实例，并支持可选的管道行为（`Pipeline`）来处理消息拦截、日志记录、验证等横切关注点。
- **Type**: class
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `LOGGER` | `Logger` | 日志记录器 |
| `dispatcher` | `Dispatcher` | 消息分发器，用于确定消息应路由到哪些传输实例 |
| `provider` | `ServiceProvider` | 服务提供者，用于获取传输和其他依赖服务 |
| `configurator` | `Configurator` | 配置器，用于获取消息约定和传输策略 |
| `pipelineFactory` | `PipelineFactory` | 管道工厂，用于创建消息处理管道 |

## Methods
### MessageBus
> 使用服务提供者创建消息总线实例。从服务提供者中解析 `Dispatcher`、`Configurator`、`PipelineFactory`。
- **Parameters**:
  - `provider` (`ServiceProvider`): 服务提供者，必须包含 Dispatcher 服务

### MessageBus
> 使用指定的参数创建消息总线实例。
- **Parameters**:
  - `provider` (`ServiceProvider`): 服务提供者
  - `configurator` (`Configurator`): 消息总线配置选项

### publishAsync
> 以发布/订阅模式异步发布一条多播消息。消息将被发送到 `Dispatcher` 确定的所有匹配传输实例。如果启用了管道行为，消息会先经过管道处理再发送。
- **Parameters**:
  - `message` (`T`): 要发布的消息
  - `options` (`PublishOptions`): 发布选项，可以为 `null`
  - `behavior` (`Consumer<PipelineMessage<RoutedMessage<T>, Void>>`): 可选的管道行为配置回调
- **Returns**: `CompletableFuture<Void>` - 在所有传输实例完成发送后完成的 future

### sendAsync
> 以发送/命令模式异步发送一条单播消息并等待响应。消息将被发送到 `Dispatcher` 确定的第一个传输实例。如果启用了管道行为，消息会先经过管道处理再发送。
- **Parameters**:
  - `message` (`T`): 要发送的消息
  - `responseType` (`Class<R>`): 期望的响应类型
  - `callback` (`Flow.Subscriber<R>`): 可选的回调，用于接收响应或错误
  - `options` (`SendOptions`): 发送选项，可以为 `null`
  - `behavior` (`Consumer<PipelineMessage<RoutedMessage<T>, R>>`): 可选的管道行为配置回调
- **Returns**: `CompletableFuture<Void>` - 在消息处理完毕时完成的 future

### callAsync
> 以请求/响应模式异步发送一条请求消息并期待类型化的响应。消息将被发送到 `Dispatcher` 确定的第一个传输实例。如果启用了管道行为，消息会先经过管道处理再发送。
- **Parameters**:
  - `request` (`T`): 请求消息
  - `responseType` (`Class<R>`): 期望的响应类型
  - `options` (`CallOptions`): 调用选项，可以为 `null`
  - `behavior` (`Consumer<PipelineMessage<RoutedMessage<T>, R>>`): 可选的管道行为配置回调
- **Returns**: `CompletableFuture<R>` - 在收到响应时完成并携带响应结果的 future
