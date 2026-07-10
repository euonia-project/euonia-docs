# MessageContextBase

> `MessageContext` 的内置实现。提供线程安全的消息处理上下文，支持基于事件的已回复、已完成和失败状态通知。在调用 `close()` 时，上下文会自动调用 `complete(Object)` 并传入原始消息，以标志消息处理结束。

- **Type**: class
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `message` | `Object` | 消息负载。 |
| `headers` | `Map<String, String>` | 消息头字典。 |
| `user` | `UserPrincipal` | 当前用户主体。 |
| `metadata` | `MessageMetadata` | 消息元数据。 |
| `disposed` | `boolean` | 是否已释放。 |
| `publisher` | `SubmissionPublisher<MessageRepliedEvent>` | 消息已回复事件的发布者。 |
| `onCompletedConsumers` | `List<Consumer<MessageHandledEvent>>` | 消息处理完成事件的消费者列表。 |

## Methods

### MessageContextBase

> 使用指定的消息初始化新实例。

- **Parameters**:
  - `message` (`Object`): 消息负载

### MessageContextBase

> 从路由消息信封初始化新实例，将所有信封元数据（ID、授权信息）复制到上下文中。

- **Parameters**:
  - `pack` (`MessageEnvelope<?>`): 路由消息信封

### onReplied

> 注册消息已回复事件的订阅者。

- **Parameters**:
  - `subscriber` (`Flow.Subscriber<? super MessageRepliedEvent>`): 消息已回复事件的订阅者

### addCompletedSubscriber

> 添加消息处理完成事件的消费者。

- **Parameters**:
  - `consumer` (`Consumer<MessageHandledEvent>`): 消息处理完成事件的消费者

### removeCompletedSubscriber

> 移除消息处理完成事件的消费者。

- **Parameters**:
  - `consumer` (`Consumer<MessageHandledEvent>`): 要移除的消费者

### getMessage

- **Returns**: `Object` - the message

### getMessageId / setMessageId

> Gets/sets the message ID from headers.

### getCorrelationId / setCorrelationId

> Gets/sets the correlation ID from headers.

### getConversationId / setConversationId

> Gets/sets the conversation ID from headers.

### getRequestTraceId / setRequestTraceId

> Gets/sets the request trace ID from headers.

### getAuthorization / setAuthorization

> Gets/sets the authorization from headers.

### getUser

- **Returns**: `UserPrincipal` - the user

### getHeaders

- **Returns**: `Map<String, String>` - unmodifiable map of headers

### getMetadata / setMetadata

> Gets/sets the message metadata.

### response

> 触发已回复事件，通知监听器消息已使用给定的响应进行了回复。

- **Parameters**:
  - `message` (`R`): 响应消息

### failure

> 触发失败事件，通知监听器消息处理遇到错误。

- **Parameters**:
  - `throwable` (`Throwable`): 导致失败的异常

### complete

> 触发已完成事件，通知监听器消息已完全处理。

- **Parameters**:
  - `message` (`Object`): 已处理的消息

### complete

> 触发已完成事件，同时携带处理器类型信息。

- **Parameters**:
  - `message` (`Object`): 已处理的消息
  - `handlerType` (`Class<?>`): 处理该消息的处理器类型

### close

> 释放上下文，使用原始消息触发已完成事件并清理所有已注册的监听器。此方法对应 .NET 的 dispose 模式：关闭时，上下文发出消息处理完成的信号并释放所有事件处理器。
