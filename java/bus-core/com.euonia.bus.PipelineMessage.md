# PipelineMessage
> 管道消息封装类，将消息与 `Pipeline` 关联，支持链式调用管道步骤并异步执行。
- **Type**: class
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `message` | `M` | 原始消息对象 |
| `pipeline` | `Pipeline<M, R>` | 关联的管道实例 |

## Methods
### PipelineMessage
> 仅使用消息创建 `PipelineMessage` 实例，管道需后续通过 `use(Class, Object...)` 设置。
- **Parameters**:
  - `message` (`M`): 消息对象

### PipelineMessage
> 使用消息和管道创建 `PipelineMessage` 实例。
- **Parameters**:
  - `message` (`M`): 消息对象
  - `pipeline` (`Pipeline<M, R>`): 关联的管道实例

### getMessage
> 获取原始消息对象。
- **Returns**: `M` - 消息对象

### getPipeline
> 获取关联的管道实例。
- **Returns**: `Pipeline<M, R>` - 管道实例，可能为 `null`

### use
> 向管道中添加一个步骤类型，并返回当前实例以支持链式调用。
- **Parameters**:
  - `type` (`Class<?>`): 管道步骤的类型
  - `args` (`Object...`): 管道步骤的构造参数
- **Returns**: `PipelineMessage<M, R>` - 当前 PipelineMessage 实例

### executeAsync
> 异步执行管道并将结果包装为 `CompletableFuture`。
- **Returns**: `CompletableFuture<R>` - 包含管道执行结果的 CompletableFuture
