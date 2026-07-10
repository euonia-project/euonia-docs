# Enqueue
> 标记消息应入队等待处理。{@code value} 属性指定了队列名称，
> {@code priority} 属性可用于指示消息的处理优先级，值越高优先级越高。
> <p>
> 此注解通常与消息总线或队列系统配合使用，以确保消息按正确顺序和适当的紧急程度进行处理。
- **Type**: annotation
- **Package**: `com.euonia.bus.annotation`
- **Author**: damon(zhaorong@outlook.com)

## Elements
| Element | Type | Default | Description |
| --- | --- | --- | --- |
| `value` | `String` | - | 队列名称。 |
| `priority` | `int` | `0` | 消息的处理优先级，值越高优先级越高，默认值为 0。 |