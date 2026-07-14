# Subscribe

> 标记方法为消息订阅处理器，指定要订阅的通道和分组名称。

- **Type**: annotation
- **Package**: `com.euonia.bus.annotation`
- **Target**: *METHOD* — 可应用于方法
- **Retention**: *RUNTIME* — 运行时保留
- **Author**: damon(zhaorong@outlook.com)

## Elements

| Element | Type | Default | Description |
|---------|------|---------|-------------|
| `value` | `String` | `""` | 要订阅的通道名称。 |
| `group` | `String` | `""` | 此订阅的分组名称。发布到同一通道但分组名称不同的消息将投递给不同的订阅者，而发布到同一通道和分组名称的消息将在同组订阅者之间负载均衡。 |
