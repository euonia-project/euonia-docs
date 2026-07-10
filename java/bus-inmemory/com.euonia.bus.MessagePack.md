# MessagePack

> 定义用于内存传输的消息包，将路由消息与其处理上下文封装在一起。

- **Type**: `class`
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Name | Type | Modifiers | Description |
|------|------|-----------|-------------|
| `message` | `MessageEnvelope<?>` | `private final` | 路由消息信封。 |
| `context` | `MessageContext` | `private final` | 消息处理上下文。 |
| `aborted` | `boolean` | `private` | 消息是否已被中止。 |

## Methods

| Name | Return Type | Parameters | Description |
|------|-------------|------------|-------------|
| `MessagePack` *(constructor)* | — | `MessageEnvelope<?> message, MessageContext context` | 使用指定的消息和上下文初始化新实例。 |
| `getMessage` | `MessageEnvelope<?>` | — | 获取路由消息信封。 |
| `getContext` | `MessageContext` | — | 获取消息处理上下文。 |
| `isAborted` | `boolean` | — | 获取消息是否已被中止。 |
| `setAborted` | `void` | `boolean aborted` | 设置此消息包的中止标志。 |
