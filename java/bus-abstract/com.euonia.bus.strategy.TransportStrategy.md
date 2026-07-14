# TransportStrategy

> 定义传输策略的契约，该策略决定了消息在出站和入站操作中的处理方式。

- **Type**: interface
- **Package**: `com.euonia.bus.strategy`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### `getName(): String`
> 获取传输策略的名称。

**Returns:** `String` — 传输策略的名称

### `allowOutgoing(String channel, Class<?> messageType): boolean`
> 判断传输策略是否允许在指定通道上发送出站消息。

**Parameters:**
- `channel` (`String`): 通道名称
- `messageType` (`Class<?>`): 消息类型

**Returns:** `boolean` — 如果传输策略允许在指定通道上发送出站消息则返回 true，否则返回 false

### `allowIncoming(String channel, Class<?> messageType): boolean`
> 判断传输策略是否允许在指定通道上接收入站消息。

**Parameters:**
- `channel` (`String`): 通道名称
- `messageType` (`Class<?>`): 消息类型

**Returns:** `boolean` — 如果传输策略允许在指定通道上接收入站消息则返回 true，否则返回 false
