# Multicast

> 标记消息为多播消息，表示消息将发送给多个订阅者。
> 所有订阅了该消息类型的订阅者都会收到该消息。
> 多播消息通常用于需要广播到多个订阅者且不期望响应的事件或通知。

- **Type**: annotation
- **Package**: `com.euonia.bus.annotation`
- **Target**: `@Target({ElementType.TYPE})` — 可应用于类/接口
- **Retention**: `@Retention(RetentionPolicy.RUNTIME)` — 运行时保留
- **Author**: damon(zhaorong@outlook.com)

## Elements

> 此注解不包含任何元素，仅作为标记注解使用。
