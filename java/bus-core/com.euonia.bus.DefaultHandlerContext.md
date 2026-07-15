# DefaultHandlerContext
> 默认的消息处理器上下文，使用 Euonia 的 `ServiceProvider` 进行依赖解析。该类管理处理器注册并将传入的消息分派到适当的处理器。它支持泛型处理器类型注册（通过 DI 解析）和基于反射的注册（通过 `ChannelRegistration`）。
- **Type**: class
- **Package**: `com.euonia.bus.handle`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `LOGGER` | `Logger` | 日志记录器 |
| `handlerContainer` | `ConcurrentMap<String, List<HandlerRegistration>>` | 处理器容器 |
| `publisher` | `SubmissionPublisher<MessageSubscribedEvent>` | 消息订阅事件发布者 |
| `convention` | `MessageConvention` | 消息约定 |
| `inboxStore` | `InboxStore` | 收件箱存储 |
| `idempotentHandler` | `IdempotentHandler` | 幂等处理器 |

## Methods
### DefaultHandlerContext
> 初始化 `DefaultHandlerContext` 的新实例。
- **Parameters**:
  - `provider` (`ServiceProvider`): 用于解析处理器和其他服务的服务提供者

### onMessageSubscribed
> 订阅消息订阅事件。
- **Parameters**:
  - `listener` (`Consumer<MessageSubscribedEvent>`): 事件监听器

### register
> 为给定的消息类型注册一个消息处理器类型。处理器将在分发时从 `ServiceProvider` 中解析。
- **Parameters**:
  - `channel` (`String`): 要注册处理器的通道名称
  - `messageType` (`Class<M>`): 消息的类
  - `handlerType` (`Class<H>`): 处理器的类

### register
> 注册由 `ChannelHandler` 描述的处理器。该注册包含处理器类型、要调用的方法和通道名称。
- **Parameters**:
  - `channel` (`String`): 要注册处理器的通道名称
  - `channelHandler` (`ChannelHandler`): 描述要注册的处理器的 ChannelHandler

### handleAsync
> 处理异步消息。对于单播消息使用单个处理器，对于多播消息并行执行所有处理器。
- **Parameters**:
  - `channel` (`String`): 通道名称
  - `recipient` (`String`): 接收者
  - `envelope` (`MessageEnvelope<?>`): 消息信封
  - `context` (`MessageContext`): 消息上下文
- **Returns**: `CompletableFuture<Object>` - 处理结果 future
