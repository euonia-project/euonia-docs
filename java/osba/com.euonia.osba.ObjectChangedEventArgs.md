# ObjectChangedEventArgs

> 表示业务对象属性更改或集合更改事件的参数。该类包含有关更改的对象、属性更改事件、集合更改类型和集合索引的信息。

- **Type**: class
- **Package**: `com.euonia.osba`
- **Author**: damon(zhaorong@outlook.com)

## Constructors

### `ObjectChangedEventArgs(Object changedObject)`

> 使用指定的已更改对象创建 ObjectChangedEventArgs 的新实例。

**Parameters:**
- `changedObject` (`Object`): 发生更改的对象

### `ObjectChangedEventArgs(Object changedObject, PropertyChangeEvent propertyChangedEvent, CollectionChangeType collectionChangeType, int collectionIndex)`

> 使用指定的已更改对象、属性更改事件、集合更改类型和集合索引创建 ObjectChangedEventArgs 的新实例。

**Parameters:**
- `changedObject` (`Object`): 发生更改的对象
- `propertyChangedEvent` (`PropertyChangeEvent`): 属性变更事件
- `collectionChangeType` (`CollectionChangeType`): 集合变更类型
- `collectionIndex` (`int`): 集合索引

## Methods

### `getChangedObject(): Object`

> 获取发生更改的对象。

**Returns:** `Object` — 发生更改的对象

### `getPropertyChangedEvent(): PropertyChangeEvent`

> 获取属性变更事件。

**Returns:** `PropertyChangeEvent` — 属性变更事件，如果没有属性变更事件则返回 null

### `getCollectionChangeType(): CollectionChangeType`

> 获取集合变更类型。

**Returns:** `CollectionChangeType` — 集合变更类型，如果没有集合变更则返回 null

### `getCollectionIndex(): int`

> 获取集合索引。

**Returns:** `int` — 集合索引，如果没有集合变更则返回 -1

## Inner Enums

### CollectionChangeType

> 集合变更类型枚举。

| Constant | Description |
|----------|-------------|
| `ADD` | 添加元素 |
| `REMOVE` | 移除元素 |
| `REPLACE` | 替换元素 |
| `CLEAR` | 清空集合 |
