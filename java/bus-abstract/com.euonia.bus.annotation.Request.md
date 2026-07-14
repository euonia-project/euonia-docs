# Request

> 标记消息为请求消息，表示消息将被发送到一个或多个订阅者并期望收到响应。
> 总线会确保订阅者能够将响应发送回发送者。
> 响应的类型由 `responseType` 属性指定，指示订阅者在收到请求消息后应返回的响应类型。

- **Type**: annotation
- **Package**: `com.euonia.bus.annotation`
- **Target**: `@Target({ElementType.TYPE})` — 可应用于类/接口
- **Retention**: `@Retention(RetentionPolicy.RUNTIME)` — 运行时保留
- **Author**: damon(zhaorong@outlook.com)

## Elements

| Element | Type | Default | Description |
|---------|------|---------|-------------|
| `responseType` | `Class<?>` | (required) | 期望的响应类型。 |
