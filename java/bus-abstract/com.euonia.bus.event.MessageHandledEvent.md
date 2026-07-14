# MessageHandledEvent

> 消息已处理事件，表示消息已被处理器处理完成。

- **Type**: class
- **Package**: `com.euonia.bus.event`
- **Author**: damon(zhaorong@outlook.com)
- **Extends**: `MessageProcessedEvent`

## Constructors

### `MessageHandledEvent(Object message)`
> 使用已处理的消息构造事件。

**Parameters:**
- `message` (`Object`): 已处理的消息

## Methods

### `getHandlerType(): Class<?>`
> 获取处理该消息的处理器类型。

**Returns:** `Class<?>` — 处理器类型

### `setHandlerType(Class<?> handlerType): void`
> 设置处理该消息的处理器类型。

**Parameters:**
- `handlerType` (`Class<?>`): 处理器类型

### `getMessage(): Object`
> 返回已处理的消息。

**Returns:** `Object` — 消息对象
