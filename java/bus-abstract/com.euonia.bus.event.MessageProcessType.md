# MessageProcessType
> {@link MessageProcessType} 是定义消息系统中可能发生的消息处理事件类型的枚举。
> 包含六个值，分别代表消息处理的不同阶段。
> 此枚举可用于以一致的方式对消息处理相关事件进行分类和处理。
- **Type**: enum
- **Package**: `com.euonia.bus.event`
- **Author**: damon(zhaorong@outlook.com)

## Enum Constants
| Constant | Description |
| --- | --- |
| `SEND` | 消息已发送 |
| `DELIVERED` | 消息已投递 |
| `RECEIVED` | 消息已接收 |
| `ACKNOWLEDGED` | 消息已确认 |
| `REPLIED` | 消息已回复 |