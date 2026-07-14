# MessageContext

> 消息上下文接口，提供消息处理过程中所需的上下文信息，包括消息标识、关联标识、会话标识、请求追踪标识、授权信息、用户主体、消息头、元数据以及响应/失败/完成回调。
>
> 此接口继承 `AutoCloseable`，允许在消息处理完成后释放相关资源。

- **Type**: interface
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)
- **Extends**: `AutoCloseable`

## Methods

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

**Returns:** `UserPrincipal` — 用户主体，可能为 `null`

### `getHeaders(): Map<String, String>`

> 获取消息头字典。

**Returns:** `Map<String, String>` — 包含所有消息头的不可变映射

### `getMetadata(): MessageMetadata`

> 获取消息元数据。

**Returns:** `MessageMetadata` — 消息元数据，可能为 `null`

### `setMetadata(MessageMetadata metadata): void`

> 设置消息元数据。

**Parameters:**
- `metadata` (`MessageMetadata`): 消息元数据

### `response(R message): void`

> 发送响应消息。

**Type Parameters:** `<R>` — 响应消息类型

**Parameters:**
- `message` (`R`): 响应消息

### `failure(Throwable throwable): void`

> 通知消息处理失败。

**Parameters:**
- `throwable` (`Throwable`): 处理过程中抛出的异常

### `complete(Object message): void`

> 完成消息处理并发送最终响应。

**Parameters:**
- `message` (`Object`): 响应消息

### `complete(Object message, Class<?> handlerType): void`

> 完成消息处理并发送最终响应，同时指定处理器类型。

**Parameters:**
- `message` (`Object`): 响应消息
- `handlerType` (`Class<?>`): 处理器类型
