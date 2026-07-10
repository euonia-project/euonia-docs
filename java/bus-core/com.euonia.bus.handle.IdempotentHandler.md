# IdempotentHandler
> 收件箱处理器，在处理消息前检查 `InboxStore` 是否已处理该消息以确保幂等性，并对失败消息进行定时重试。
- **Type**: class
- **Package**: `com.euonia.bus.handle`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `LOGGER` | `Logger` | 日志记录器 |
| `inboxStore` | `InboxStore` | 收件箱存储 |
| `scheduler` | `ScheduledExecutorService` | 调度线程池 |
| `provider` | `ServiceProvider` | 服务提供者 |
| `pipelineFactory` | `PipelineFactory` | 管道工厂 |
| `handlerContainer` | `Map<String, List<HandlerRegistration>>` | 处理器容器 |
| `runningLock` | `AtomicInteger` | 运行锁 |

## Methods
### IdempotentHandler
> 构造方法。
- **Parameters**:
  - `provider` (`ServiceProvider`): 服务提供者
  - `handlerContainer` (`Map<String, List<HandlerRegistration>>`): 处理器容器

### start
> 启动收件箱处理器，开始定时重试失败消息（每60秒）。

### executeHandlerAsync
> 在给定的服务范围内异步执行单个处理器注册项。
- **Parameters**:
  - `registration` (`HandlerRegistration`): 处理器注册项
  - `message` (`MessageEnvelope<?>`): 消息对象
  - `context` (`MessageContext`): 消息上下文
- **Returns**: `CompletableFuture<Object>` - 异步处理结果

### executeHandler
> 在给定的服务范围内执行单个处理器注册项。
- **Parameters**:
  - `registration` (`HandlerRegistration`): 处理器注册项
  - `message` (`MessageEnvelope<?>`): 消息对象
  - `context` (`MessageContext`): 消息上下文
- **Returns**: `Object` - 处理结果
