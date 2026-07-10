# Handler
> 定义处理特定类型消息并返回响应的契约。
- **Type**: interface
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Type Parameters
| Parameter | Description |
|-----------|-------------|
| `M` | 要处理的消息类型，必须继承 `Message` |
| `R` | 处理消息后返回的响应类型 |

## Methods
### handle
> 处理类型为 M 的消息并返回类型为 R 的响应。
- **Parameters**:
  - `message` (`M`): 要处理的消息
  - `context` (`MessageContext`): 处理消息的上下文
- **Returns**: `R` - 处理消息后的响应
