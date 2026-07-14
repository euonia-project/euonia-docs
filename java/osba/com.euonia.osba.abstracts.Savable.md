# Savable

> 标记一个可以保存到数据库或其他持久化存储的对象。

- **Type**: interface
- **Package**: `com.euonia.osba.abstracts`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<T>` — 被保存对象的类型

## Methods

### saveComplete(T newObject): void

> 保存对象的完整状态到数据库或其他持久化存储。

**Parameters:**
- `newObject` (`T`): 要保存的对象

### save(boolean forceUpdate): T

> 保存对象的状态到数据库或其他持久化存储。

**Parameters:**
- `forceUpdate` (`boolean`): 是否强制更新

**Returns:** `T` — 保存后的对象
