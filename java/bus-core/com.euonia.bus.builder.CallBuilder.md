# CallBuilder
> 请求/响应模式的 Builder。
- **Type**: class
- **Package**: `com.euonia.bus.builder`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `bus` | `Bus` | 消息总线 |
| `request` | `T` | 请求消息 |
| `responseType` | `Class<R>` | 响应类型 |
| `behavior` | `Consumer<PipelineMessage<RoutedMessage<T>, R>>` | 管道行为配置回调 |
| `options` | `CallOptions` | 调用选项 |

## Methods
### CallBuilder
> 构造方法。
- **Parameters**:
  - `bus` (`Bus`): 消息总线
  - `request` (`T`): 请求消息
  - `responseType` (`Class<R>`): 响应类型

### withChannel
> 指定消息所属通道。
- **Parameters**:
  - `channel` (`String`): 通道名
- **Returns**: `CallBuilder<T, R>` - 当前实例

### withBehavior
> 配置管道行为回调。
- **Parameters**:
  - `behavior` (`Consumer<PipelineMessage<RoutedMessage<T>, R>>`): 管道行为回调
- **Returns**: `CallBuilder<T, R>` - 当前实例

### withMetadata
> 配置元数据设置器。
- **Parameters**:
  - `metadataSetter` (`Consumer<MessageMetadata>`): 元数据设置器
- **Returns**: `CallBuilder<T, R>` - 当前实例

### withMessageId
> 指定请求的 messageId。
- **Parameters**:
  - `messageId` (`String`): 请求的 messageId
- **Returns**: `CallBuilder<T, R>` - 当前实例

### withCorrelationId
> 指定消息的关联 ID。
- **Parameters**:
  - `correlationId` (`String`): 关联 ID
- **Returns**: `CallBuilder<T, R>` - 当前实例

### withPriority
> 指定消息优先级，数值越大优先级越高。
- **Parameters**:
  - `priority` (`int`): 优先级
- **Returns**: `CallBuilder<T, R>` - 当前实例

### withTimeout
> 指定消息的超时时间，单位为毫秒。
- **Parameters**:
  - `timeoutMillis` (`long`): 超时时间（毫秒）
- **Returns**: `CallBuilder<T, R>` - 当前实例

### withDelay
> 指定消息的延迟发送时间，单位为毫秒。
- **Parameters**:
  - `delayMillis` (`long`): 延迟发送时间（毫秒）
- **Returns**: `CallBuilder<T, R>` - 当前实例

### executeAsync
> 执行请求。
- **Returns**: `CompletableFuture<R>` - 在收到响应时完成并携带响应结果的 future
