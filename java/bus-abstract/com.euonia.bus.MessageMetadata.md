# MessageMetadata

> 消息元数据容器，封装了一个 `Map` 用于存储消息的附加元数据。除了实现 `Map` 接口外，还提供了类型安全的 `get(String, Class)` 方法，在获取值时进行类型检查，如果类型不匹配则抛出 `IllegalStateException`。

- **Type**: class
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `metadata` | `Map<String, Object>` | 底层元数据存储 |

## Methods

### get

> 根据键获取元数据值，如果键不存在则返回 null。

- **Parameters**:
  - `key` (`String`): 元数据键
- **Returns**: `Object` - 元数据值，如果键不存在则返回 null

### get

> 根据键获取元数据值，并在返回值时进行类型强制转换。如果键不存在则返回 null；如果值类型不匹配则抛出 `IllegalStateException`。

- **Parameters**:
  - `key` (`String`): 元数据键
  - `type` (`Class<T>`): 期望的值类型
- **Returns**: `T` - 强制转换为指定类型的元数据值
- **Throws**: `IllegalStateException` - 如果值存在但类型不匹配

### size, isEmpty, containsKey, containsValue, put, remove, putAll, clear, keySet, values, entrySet

> Standard `Map` interface implementations.
