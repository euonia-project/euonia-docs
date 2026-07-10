# ExtendableOptions
> 消息发送和接收的默认选项，用户可以扩展此类以添加自定义选项。
- **Type**: abstract class
- **Package**: `com.euonia.bus.options`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `messageId` | `String` | 消息的唯一标识符 |
| `channel` | `String` | 消息所属的通道名称 |
| `queue` | `String` | 消息所属的队列名称 |
| `priority` | `int` | 消息的优先级 |
| `enablePipelineBehaviors` | `Boolean` | 管道行为是否启用（null 表示使用全局配置） |
| `attachDefaultPipelineBehaviors` | `boolean` | 是否附加默认管道行为 |
| `delay` | `long` | 延迟发送时间（毫秒） |
| `timeout` | `long` | 超时时间（毫秒） |
| `metadataSetter` | `Consumer<MessageMetadata>` | 元数据设置器 |

## Methods
### getMessageId / setMessageId
> 获取/设置消息的唯一标识符，可用于消息追踪和关联。

### getChannel / setChannel
> 获取/设置消息所属的通道名称，可用于消息路由和分类。

### getQueue / setQueue
> 获取/设置消息所属的队列名称，可用于消息路由和分类。

### getPriority / setPriority
> 获取/设置消息的优先级，可用于消息排序和处理。

### isEnablePipelineBehaviors / setEnablePipelineBehaviors
> 检查/设置管道行为是否已启用，可用于自定义消息处理。

### isAttachDefaultPipelineBehaviors / setAttachDefaultPipelineBehaviors
> 检查/设置默认管道行为是否已附加，可用于自定义消息处理。

### getDelay / setDelay
> 获取/设置延迟时间。

### getTimeout / setTimeout
> 获取/设置超时时间。

### getMetadataSetter / setMetadataSetter
> 获取/设置元数据设置器。
