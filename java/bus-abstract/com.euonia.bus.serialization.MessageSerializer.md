# MessageSerializer

> 消息序列化器接口，定义了消息的序列化和反序列化方法。
> 实现该接口的类可以使用不同的序列化方式（如JSON、XML、Protobuf等）来处理消息的序列化和反序列化。

- **Type**: interface
- **Package**: `com.euonia.bus.serialization`
- **Author**: damon(zhaorong@outlook.com)

> **Note:** 该接口提供了两种序列化方式：字符串和字节数组。实现类可以根据需要选择适合的序列化方式。

## Methods

### `<M> serialize(M message): String`
> 将消息对象序列化为字符串。

**Type Parameters:**
- `<M>` — 消息对象的类型

**Parameters:**
- `message` (`M`): 消息对象

**Returns:** `String` — 序列化后的字符串

### `<M> deserialize(String data, Class<M> type): M`
> 将字符串反序列化为消息对象。

**Type Parameters:**
- `<M>` — 消息对象的类型

**Parameters:**
- `data` (`String`): 序列化后的字符串
- `type` (`Class<M>`): 消息对象的类型

**Returns:** `M` — 反序列化后的消息对象

### `<M> deserialize(String data, Type type): M`
> 将字符串反序列化为消息对象（支持泛型类型）。
> 当需要反序列化的目标类型包含泛型参数时（如 `RoutedMessage<ConcretePayload>`），应优先使用此方法以确保类型信息不会丢失。

**Type Parameters:**
- `<M>` — 消息对象的类型

**Parameters:**
- `data` (`String`): 序列化后的字符串
- `type` (`Type`): 消息对象的类型（支持参数化类型）

**Returns:** `M` — 反序列化后的消息对象

### `deserialize(String data): Object`
> 将字符串反序列化为消息对象（类型未知）。

**Parameters:**
- `data` (`String`): 序列化后的字符串

**Returns:** `Object` — 反序列化后的消息对象

### `<M> serializeToBytes(M message): byte[]`
> 将消息对象序列化为字节数组。

**Type Parameters:**
- `<M>` — 消息对象的类型

**Parameters:**
- `message` (`M`): 消息对象

**Returns:** `byte[]` — 序列化后的字节数组

### `<M> deserializeFromBytes(byte[] data, Class<M> type): M`
> 将字节数组反序列化为消息对象。

**Type Parameters:**
- `<M>` — 消息对象的类型

**Parameters:**
- `data` (`byte[]`): 序列化后的字节数组
- `type` (`Class<M>`): 消息对象的类型

**Returns:** `M` — 反序列化后的消息对象

### `deserializeFromBytes(byte[] data): Object`
> 将字节数组反序列化为消息对象（类型未知）。

**Parameters:**
- `data` (`byte[]`): 序列化后的字节数组

**Returns:** `Object` — 反序列化后的消息对象

### `<V> serializeEnvelope(MessageEnvelope<V> envelope): String`
> 将消息信封序列化为字符串。

**Type Parameters:**
- `<V>` — 消息负载的类型

**Parameters:**
- `envelope` (`MessageEnvelope<V>`): 消息信封

**Returns:** `String` — 序列化后的字符串

### `<V> deserializeEnvelope(String data, Class<V> payloadType): MessageEnvelope<V>`
> 将消息信封反序列化为消息对象。

**Type Parameters:**
- `<V>` — 消息负载的类型

**Parameters:**
- `data` (`String`): 序列化后的字符串
- `payloadType` (`Class<V>`): 消息负载的类型

**Returns:** `MessageEnvelope<V>` — 反序列化后的消息信封
