# ChannelHandler

> 表示一个消息处理器，封装了处理器类型、方法和实例。

- **Type**: record
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Record Components

| Component | Type | Description |
|-----------|------|-------------|
| `handlerType` | `Class<?>` | 处理器的类型 |
| `method` | `Method` | 要调用的方法 |
| `instance` | `Object` | 处理器的实例 |
