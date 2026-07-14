# Channel

> 指定消息处理器订阅的通道名称。
> 可应用于类型或参数级别，在运行时保留以便消息总线框架通过反射获取。

- **Type**: annotation
- **Package**: `com.euonia.bus.annotation`
- **Target**: *TYPE*, *PARAMETER* — 可应用于类/接口或参数
- **Retention**: *RUNTIME* — 运行时保留
- **Author**: damon(zhaorong@outlook.com)

## Elements

| Element | Type | Default | Description |
|---------|------|---------|-------------|
| `value` | `String` | (required) | 通道名称。 |
