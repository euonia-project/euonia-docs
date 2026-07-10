# InboxCompletionBehavior
> (package-private) 管道行为实现，在处理器执行后根据结果标记 InboxStore 中消息的成功或失败状态。
- **Type**: class
- **Package**: `com.euonia.bus.handle`
- **Author**: (not specified)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `inboxStore` | `InboxStore` | 收件箱存储 |

## Methods
### InboxCompletionBehavior
> 构造方法。
- **Parameters**:
  - `inboxStore` (`InboxStore`): 收件箱存储

### handleAsync
> 执行管道下一步，并在完成后根据结果标记消息状态。
- **Parameters**:
  - `context` (`Duet<String, MessageEnvelope<?>>`): 包含处理器名和消息信封的上下文
  - `next` (`PipelineDelegate<Duet<String, MessageEnvelope<?>>, Object>`): 管道下一步委托
- **Returns**: `CompletionStage<Object>` - 异步执行结果
