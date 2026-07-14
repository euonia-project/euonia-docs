# ChannelRegistration

> `ChannelRegistration` 表示特定通道和消息类型的处理器注册信息。
>
> 包含消息类型和对应的处理器列表，支持通过 `addHandler(ChannelHandler)`
> 方法以流式方式添加处理器。

- **Type**: class
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Constructors

### `ChannelRegistration(Class<?> messageType)`

> 使用指定的消息类型构造通道注册信息。

**Parameters:**
- `messageType` (`Class<?>`): 消息类型

## Methods

### `getMessageType(): Class<?>`

> 获取消息类型。

**Returns:** `Class<?>` — 消息类型

### `getHandlers(): List<ChannelHandler>`

> 获取处理器列表的不可修改视图。

**Returns:** `List<ChannelHandler>` — 处理器列表

### `addHandler(ChannelHandler handler): ChannelRegistration`

> 添加处理器并返回当前实例以支持链式调用。

**Parameters:**
- `handler` (`ChannelHandler`): 要添加的处理器

**Returns:** `ChannelRegistration` — 当前 ChannelRegistration 实例
