# SendBuilder
> 发送/命令模式的 Builder。
- **Type**: class
- **Package**: `com.euonia.bus.builder`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `bus` | `Bus` | 消息总线 |
| `message` | `T` | 消息负载 |
| `responseType` | `Class<R>` | 响应类型 |
| `callback` | `Flow.Subscriber<R>` | 响应回调 |
| `behavior` | `Consumer<PipelineMessage<RoutedMessage<T>, R>>` | 管道行为配置回调 |
| `options` | `SendOptions` | 发送选项 |

## Methods
### SendBuilder
> 构造方法。
- **Parameters**:
  - `bus` (`Bus`): 消息总线
  - `message` (`T`): 消息负载
  - `responseType` (`Class<R>`): 响应类型

### withChannel
> 指定消息所属通道。
- **Parameters**:
  - `channel` (`String`): 通道名
- **Returns**: `SendBuilder<T, R>` - 当前实例

### withCallback
> 配置响应回调（兼容 Flow.Subscriber）。
- **Parameters**:
  - `callback` (`Flow.Subscriber<R>`): 回调
- **Returns**: `SendBuilder<T, R>` - 当前实例

### withBehavior
> 配置管道行为回调。
- **Parameters**:
  - `behavior` (`Consumer<PipelineMessage<RoutedMessage<T>, R>>`): 管道行为回调
- **Returns**: `SendBuilder<T, R>` - 当前实例

### withMetadata
> 配置元数据设置器。
- **Parameters**:
  - `metadataSetter` (`Consumer<MessageMetadata>`): 元数据设置器
- **Returns**: `SendBuilder<T, R>` - 当前实例

### withMessageId
> 指定消息 ID。
- **Parameters**:
  - `messageId` (`String`): 消息 ID
- **Returns**: `SendBuilder<T, R>` - 当前实例

### withCorrelationId
> 指定消息的关联 ID。
- **Parameters**:
  - `correlationId` (`String`): 关联 ID
- **Returns**: `SendBuilder<T, R>` - 当前实例

### withPriority
> 指定消息优先级，数值越大优先级越高。
- **Parameters**:
  - `priority` (`int`): 消息优先级
- **Returns**: `SendBuilder<T, R>` - 当前实例

### withTimeout
> 指定消息的超时时间，单位为毫秒。
- **Parameters**:
  - `timeoutMillis` (`long`): 超时时间（毫秒）
- **Returns**: `SendBuilder<T, R>` - 当前实例

### withDelay
> 指定消息的延迟发送时间，单位为毫秒。
- **Parameters**:
  - `delayMillis` (`long`): 延迟发送时间（毫秒）
- **Returns**: `SendBuilder<T, R>` - 当前实例

### runAsync
> 执行发送。
- **Returns**: `CompletableFuture<Void>` - 在消息处理完毕时完成的 future
