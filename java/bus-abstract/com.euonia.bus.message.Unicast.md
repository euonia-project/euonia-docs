# Unicast

> `Unicast` 是一个标记接口，表示消息仅针对单个接收者。
> <p>
> 实现此接口的消息将被视为单播消息，即使为同一消息类型注册了多个订阅者，
> 也只会投递给一个订阅者。这适用于消息只能由一个处理器处理的场景，
> 例如需要单一响应的命令或请求。

- **Type**: interface
- **Package**: `com.euonia.bus.message`
- **Author**: damon(zhaorong@outlook.com)
- **Extends**: `Message`

## Methods

*Inherited from `Message`.*
