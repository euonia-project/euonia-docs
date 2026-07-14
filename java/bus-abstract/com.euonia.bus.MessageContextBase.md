# MessageContextBase

> `MessageContext` 的内置实现。
>
> 提供线程安全的消息处理上下文，支持基于事件的已回复、已完成和失败状态
> 通知。在调用 `close()` 时，上下文会自动调用 `complete(Object)`
> 并传入原始消息，以标志消息处理结束。

- **Type**: class
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)
- **Implements**: `MessageContext`

## Constructors

### `MessageContextBase(Object message)`

> 使用指定的消息初始化新实例。

**Parameters:**
- `message` (`Object`): 消息负载

### `MessageContextBase(MessageEnvelope<?> pack)`

> 从路由消息信封初始化新实例，将所有信封元数据（ID、授权信息）复制到
> 上下文中。

**Parameters:**
- `pack` (`MessageEnvelope<?>`): 路由消息信封

## Methods

### `onReplied(Flow.Subscriber<? super MessageRepliedEvent> subscriber): void`

> 注册消息已回复事件的订阅者。

**Type Parameters:** `<R>` — 响应类型

**Parameters:**
- `subscriber` (`Flow.Subscriber<? super MessageRepliedEvent>`): 消息已回复事件的订阅者

### `addCompletedSubscriber(Consumer<MessageHandledEvent> consumer): void`

> 添加消息处理完成事件的消费者。

**Parameters:**
- `consumer` (`Consumer<MessageHandledEvent>`): 消息处理完成事件的消费者

### `removeCompletedSubscriber(Consumer<MessageHandledEvent> consumer): void`

> 移除消息处理完成事件的消费者。

**Parameters:**
- `consumer` (`Consumer<MessageHandledEvent>`): 要移除的消费者

### `getMessage(): Object`

> 获取当前消息对象。

**Returns:** `Object` — 消息对象

### `getMessageId(): String`

> 获取消息唯一标识。

**Returns:** `String` — 消息 ID

### `setMessageId(String messageId): void`

> 设置消息唯一标识。

**Parameters:**
- `messageId` (`String`): 消息 ID

### `getCorrelationId(): String`

> 获取关联标识，用于将相关消息关联在一起。

**Returns:** `String` — 关联 ID

### `setCorrelationId(String correlationId): void`

> 设置关联标识。

**Parameters:**
- `correlationId` (`String`): 关联 ID

### `getConversationId(): String`

> 获取会话标识，用于标识一组相关的消息对话。

**Returns:** `String` — 会话 ID

### `setConversationId(String conversationId): void`

> 设置会话标识。

**Parameters:**
- `conversationId` (`String`): 会话 ID

### `getRequestTraceId(): String`

> 获取请求追踪标识，用于分布式链路追踪。

**Returns:** `String` — 请求追踪 ID

### `setRequestTraceId(String requestTraceId): void`

> 设置请求追踪标识。

**Parameters:**
- `requestTraceId` (`String`): 请求追踪 ID

### `getAuthorization(): String`

> 获取授权信息（如 Bearer token）。

**Returns:** `String` — 授权字符串

### `setAuthorization(String authorization): void`

> 设置授权信息。

**Parameters:**
- `authorization` (`String`): 授权字符串

### `getUser(): UserPrincipal`

> 获取当前用户主体信息。

**Returns:** `UserPrincipal` — 用户主体

### `getHeaders(): Map<String, String>`

> 获取消息头字典。

**Returns:** `Map<String, String>` — 包含所有消息头的不可变映射

### `getMetadata(): MessageMetadata`

> 获取消息元数据。

**Returns:** `MessageMetadata` — 消息元数据

### `setMetadata(MessageMetadata metadata): void`

> 设置消息元数据。

**Parameters:**
- `metadata` (`MessageMetadata`): 消息元数据

### `response(R message): void`

> 触发已回复事件，通知监听器消息已使用给定的响应进行了回复。

**Type Parameters:** `<R>` — 响应消息类型

**Parameters:**
- `message` (`R`): 响应消息

### `failure(Throwable throwable): void`

> 触发失败事件，通知监听器消息处理遇到错误。

**Parameters:**
- `throwable` (`Throwable`): 导致失败的异常

### `complete(Object message): void`

> 触发已完成事件，通知监听器消息已完全处理。

**Parameters:**
- `message` (`Object`): 已处理的消息

### `complete(Object message, Class<?> handlerType): void`

> 触发已完成事件，同时携带处理器类型信息。

**Parameters:**
- `message` (`Object`): 已处理的消息
- `handlerType` (`Class<?>`): 处理该消息的处理器类型

### `close(): void`

> 释放上下文，使用原始消息触发已完成事件并清理所有已注册的监听器。
>
> 此方法对应 .NET 的 dispose 模式：关闭时，上下文发出消息处理完成的
> 信号并释放所有事件处理器。
