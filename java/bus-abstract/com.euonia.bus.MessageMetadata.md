# MessageMetadata

> 消息元数据容器，封装了一个 `Map` 用于存储消息的附加元数据。
>
> 除了实现 `Map` 接口外，还提供了类型安全的 `get(String, Class)` 方法，
> 在获取值时进行类型检查，如果类型不匹配则抛出 `IllegalStateException`。

- **Type**: class
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)
- **Implements**: `Map<String, Object>`

## Methods

### `size(): int`

**Returns:** `int` — Map 中键值对的数量

### `isEmpty(): boolean`

**Returns:** `boolean` — 如果 Map 为空则返回 true

### `containsKey(Object key): boolean`

**Parameters:**
- `key` (`Object`): 要检查的键

**Returns:** `boolean` — 如果 Map 包含该键则返回 true

### `containsValue(Object value): boolean`

**Parameters:**
- `value` (`Object`): 要检查的值

**Returns:** `boolean` — 如果 Map 包含该值则返回 true

### `get(String key): Object`

> 根据键获取元数据值，如果键不存在则返回 null。

**Parameters:**
- `key` (`String`): 元数据键

**Returns:** `Object` — 元数据值，如果键不存在则返回 null

### `get(String key, Class<T> type): T`

> 根据键获取元数据值，并在返回值时进行类型强制转换。
>
> 如果键不存在则返回 null；如果值类型不匹配则抛出 `IllegalStateException`。

**Type Parameters:** `<T>` — 期望的值类型

**Parameters:**
- `key` (`String`): 元数据键
- `type` (`Class<T>`): 期望的值类型

**Returns:** `T` — 强制转换为指定类型的元数据值，如果键不存在则返回 null

**Throws:** `IllegalStateException` — 如果值存在但类型不匹配

### `get(Object key): Object`

**Parameters:**
- `key` (`Object`): 元数据键

**Returns:** `Object` — 元数据值，如果键不存在则返回 null

### `put(String key, Object value): Object`

**Parameters:**
- `key` (`String`): 元数据键
- `value` (`Object`): 元数据值

**Returns:** `Object` — 先前与该键关联的值，如果没有则返回 null

### `remove(Object key): Object`

**Parameters:**
- `key` (`Object`): 要移除的键

**Returns:** `Object` — 先前与该键关联的值，如果没有则返回 null

### `putAll(Map<? extends String, ? extends Object> m): void`

**Parameters:**
- `m` (`Map<? extends String, ? extends Object>`): 要添加的映射

### `clear(): void`

> 移除所有映射。

### `keySet(): Set<String>`

**Returns:** `Set<String>` — Map 中所有键的集合

### `values(): Collection<Object>`

**Returns:** `Collection<Object>` — Map 中所有值的集合

### `entrySet(): Set<Entry<String, Object>>`

**Returns:** `Set<Entry<String, Object>>` — Map 中所有条目的集合
