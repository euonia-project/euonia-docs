# Dispatcher

> 定义消息分发器，用于确定消息应被派发到哪些传输通道。

- **Type**: interface
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### `determine(String channel, Class<?> messageType): List<String>`

> 确定给定通道的消息应被派发到哪些传输通道。

**Parameters:**
- `channel` (`String`): 消息的通道
- `messageType` (`Class<?>`): 消息的类型

**Returns:** `List<String>` — 传输名称列表
