# Transport

> `Transport` 负责将消息发送到系统中的其他节点。提供发布事件、发送命令和进行请求-响应调用的方法。
>
> 每种传输实现可以使用不同的底层通信协议（如 HTTP、gRPC、WebSocket 等）来发送消息。传输还负责处理消息的序列化和反序列化，以及管理连接和确保消息传递。
>
> `Transport` 接口定义了发送消息的契约，可以创建不同的实现来支持各种通信协议和模式。

- **Type**: interface
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### getName

> 获取传输名称。可用于标识当前使用的传输实现（如 "HTTP"、"gRPC"、"WebSocket" 等）。

- **Returns**: `String` - 传输名称

### publishAsync

> 向传输发布消息。此方法通常用于发送不期望响应的事件或消息。消息以异步方式发送，返回一个 `CompletableFuture`，该 Future 在消息成功发布后完成。

- **Parameters**:
  - `message` (`MessageEnvelope<M>`): 要发布的消息
- **Returns**: `CompletableFuture<Void>` - 在消息成功发布后完成的 CompletableFuture

### sendAsync

> 向指定目标发送消息。此方法通常用于发送期望响应的命令或消息。消息以异步方式发送，返回一个 `CompletableFuture`，该 Future 在消息成功发送后完成。

- **Parameters**:
  - `message` (`MessageEnvelope<M>`): 要发送的消息
- **Returns**: `CompletableFuture<Void>` - 在消息成功发送后完成的 CompletableFuture

### sendAsync

> 发送请求消息并等待响应。此方法通常用于请求-响应通信模式。`responseType` 参数指定了期望的响应消息类型，允许传输层适当处理反序列化和类型转换。

- **Parameters**:
  - `message` (`MessageEnvelope<M>`): 要发送的请求消息
  - `responseType` (`Class<R>`): 期望的响应消息类型
- **Returns**: `CompletableFuture<R>` - 在收到响应时完成的 CompletableFuture

### callAsync

> 发送请求消息并等待响应。此方法通常用于 RPC 调用模式。

- **Parameters**:
  - `message` (`MessageEnvelope<M>`): 要发送的请求消息
  - `responseType` (`Class<R>`): 期望的响应消息类型，允许传输层适当处理反序列化和类型转换
- **Returns**: `CompletableFuture<R>` - 在收到响应时完成的 CompletableFuture
