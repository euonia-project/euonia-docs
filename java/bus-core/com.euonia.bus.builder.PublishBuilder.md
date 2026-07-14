# PublishBuilder
> 发布/订阅模式的 Builder。
- **Type**: class
- **Package**: `com.euonia.bus.builder`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `bus` | `Bus` | 消息总线 |
| `message` | `T` | 消息负载 |
| `behavior` | `Consumer<PipelineMessage<RoutedMessage<T>, Void>>` | 管道行为配置回调 |
| `options` | `PublishOptions` | 发布选项 |

## Methods
### PublishBuilder
> 构造方法。
- **Parameters**:
  - `bus` (`Bus`): 消息总线
  - `message` (`T`): 消息负载

### withChannel
> 指定消息所属通道。
- **Parameters**:
  - `channel` (`String`): 通道名
- **Returns**: `PublishBuilder<T>` - 当前实例

### withBehavior
> 配置管道行为回调。
- **Parameters**:
  - `behavior` (`Consumer<PipelineMessage<RoutedMessage<T>, Void>>`): 管道行为回调
- **Returns**: `PublishBuilder<T>` - 当前实例

### withMetadata
> 配置元数据设置器。
- **Parameters**:
  - `metadataSetter` (`Consumer<MessageMetadata>`): 元数据设置器
- **Returns**: `PublishBuilder<T>` - 当前实例

### withMessageId
> 指定消息 ID。
- **Parameters**:
  - `messageId` (`String`): 消息 ID
- **Returns**: `PublishBuilder<T>` - 当前实例

### withPriority
> 指定消息优先级，数值越大优先级越高。
- **Parameters**:
  - `priority` (`int`): 消息优先级
- **Returns**: `PublishBuilder<T>` - 当前实例

### withTimeout
> 指定消息的超时时间，单位为毫秒。
- **Parameters**:
  - `timeoutMillis` (`long`): 超时时间（毫秒）
- **Returns**: `PublishBuilder<T>` - 当前实例

### withDelay
> 指定消息的延迟发送时间，单位为毫秒。
- **Parameters**:
  - `delayMillis` (`long`): 延迟发送时间（毫秒）
- **Returns**: `PublishBuilder<T>` - 当前实例

### executeAsync
> 执行发布。
- **Returns**: `CompletableFuture<Void>` - 在所有传输实例完成发送后完成的 future
