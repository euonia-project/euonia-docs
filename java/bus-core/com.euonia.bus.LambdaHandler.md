# LambdaHandler
> (package-private) 用于将 `BiFunction<T, MessageContext, R>` lambda 表达式包装为可通过反射调用的处理器实例。
- **Type**: class
- **Package**: `com.euonia.bus`
- **Author**: (not specified)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `handler` | `BiFunction<T, MessageContext, R>` | 实际处理函数 |

## Methods
### LambdaHandler
> 构造方法，使用给定的处理函数创建实例。
- **Parameters**:
  - `handler` (`BiFunction<T, MessageContext, R>`): 处理函数

### handle
> 调用内部处理函数处理消息。
- **Parameters**:
  - `message` (`T`): 消息
  - `context` (`MessageContext`): 消息上下文
- **Returns**: `R` - 处理结果
