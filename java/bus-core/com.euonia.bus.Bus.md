# Bus
> 消息总线接口，定义了消息的发布、发送和请求-响应调用的核心契约。

- **Type**: interface
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Description
提供三种消息传递模式：

- **发布/订阅（Publish）** — 通过 `publish` 构建器将多播消息发送到所有订阅者
- **发送/命令（Send）** — 通过 `send` 构建器将单播消息发送到单个处理程序
- **请求/响应（Call）** — 通过 `call` 构建器发送请求并期待类型化的响应

## Methods
### publish
> 创建发布/订阅模式的 Builder。

- **Parameters**:
  - `message` (`T`): 要发布的消息
- **Returns**: `PublishBuilder<T>` - PublishBuilder 实例

### send
> 创建发送/命令模式的 Builder（不关心响应类型）。

- **Parameters**:
  - `message` (`T`): 要发送的消息
- **Returns**: `SendBuilder<T, Void>` - SendBuilder 实例

### send
> 创建发送/命令模式的 Builder（指定响应类型）。

- **Parameters**:
  - `message` (`T`): 要发送的消息
  - `responseType` (`Class<R>`): 期望的响应类型
- **Returns**: `SendBuilder<T, R>` - SendBuilder 实例

### call
> 创建请求/响应模式的 Builder。

- **Parameters**:
  - `request` (`T`): 请求消息
  - `responseType` (`Class<R>`): 期望的响应类型
- **Returns**: `CallBuilder<T, R>` - CallBuilder 实例

### publishAsync
> 以发布/订阅模式异步发布一条多播消息（完整参数版本）。

- **Parameters**:
  - `message` (`T`): 要发布的消息
  - `options` (`PublishOptions`): 发布选项
  - `behavior` (`Consumer<PipelineMessage<RoutedMessage<T>, Void>>`): 可选的管道行为配置回调，可以为 `null`
- **Returns**: `CompletableFuture<Void>` - 在所有传输实例完成发送后完成的 future

### sendAsync
> 以发送/命令模式异步发送一条单播消息并等待响应（完整参数版本）。

- **Parameters**:
  - `message` (`T`): 要发送的消息
  - `responseType` (`Class<R>`): 期望的响应类型
  - `callback` (`Flow.Subscriber<R>`): 可选的回调，用于接收响应或错误
  - `sendOptions` (`SendOptions`): 发送选项
  - `behavior` (`Consumer<PipelineMessage<RoutedMessage<T>, R>>`): 可选的管道行为配置回调，可以为 `null`
- **Returns**: `CompletableFuture<Void>` - 在消息处理完毕时完成的 future

### callAsync
> 以请求/响应模式异步发送一条请求消息并期待类型化的响应（完整参数版本）。

- **Parameters**:
  - `request` (`T`): 请求消息
  - `responseType` (`Class<R>`): 期望的响应类型
  - `callOptions` (`CallOptions`): 调用选项
  - `behavior` (`Consumer<PipelineMessage<RoutedMessage<T>, R>>`): 可选的管道行为配置回调，可以为 `null`
- **Returns**: `CompletableFuture<R>` - 在收到响应时完成并携带响应结果的 future

### publishAsync
> 以发布/订阅模式异步发布一条多播消息。

- **Parameters**:
  - `message` (`T`): 要发布的消息
- **Returns**: `CompletableFuture<Void>` - 在所有传输实例完成发送后完成的 future

### sendAsync
> 以发送/命令模式异步发送一条单播消息并等待响应。

- **Parameters**:
  - `message` (`T`): 要发送的消息
- **Returns**: `CompletableFuture<Void>` - 在消息处理完毕时完成的 future

### sendAsync
> 以发送/命令模式异步发送一条单播消息并等待响应。

- **Parameters**:
  - `message` (`T`): 要发送的消息
  - `responseType` (`Class<R>`): 期望的响应类型
  - `callback` (`Flow.Subscriber<R>`): 可选的回调，用于接收响应或错误
- **Returns**: `CompletableFuture<Void>` - 在消息处理完毕时完成的 future

### callAsync
> 以请求/响应模式异步发送一条请求消息并期待类型化的响应。

- **Parameters**:
  - `request` (`T`): 请求消息
  - `responseType` (`Class<R>`): 期望的响应类型
- **Returns**: `CompletableFuture<R>` - 在收到响应时完成并携带响应结果的 future
