# MessageHeaders

> 消息头部常量定义，包含消息传输中常用的各种头部键名。
>
> 这些常量用于在消息传输层（如 AMQP、Kafka）中设置和读取消息的元数据信息。

- **Type**: class
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Static Fields

| Field | Value | Description |
|-------|-------|-------------|
| `CONVERSATION_ID` | `"x-conversation-id"` | 会话 ID |
| `REQUEST_TRACE_ID` | `"x-request-trace-id"` | 请求追踪 ID |
| `AUTHORIZATION` | `"x-authorization"` | 授权令牌 |
| `CORRELATION_ID` | `"x-correlation-id"` | 关联 ID |
| `MESSAGE_ID` | `"x-message-id"` | 消息 ID |
| `MESSAGE_TYPE` | `"x-message-type"` | 消息类型 |
| `CONTENT_TYPE` | `"x-content-type"` | 内容类型 |
| `CONTENT_ENCODING` | `"x-content-encoding"` | 内容编码 |
| `DELIVERY_MODE` | `"x-delivery-mode"` | 投递模式 |
| `TIMESTAMP` | `"x-timestamp"` | 时间戳 |
| `PRIORITY` | `"x-priority"` | 优先级 |
| `EXPIRATION` | `"x-expiration"` | 过期时间 |
| `REPLY_TO` | `"x-reply-to"` | 回复地址 |
| `TYPE` | `"x-type"` | 类型 |
| `USER_ID` | `"x-user-id"` | 用户 ID |
| `ROUTING_KEY` | `"x-routing-key"` | 路由键 |
