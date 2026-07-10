# ObjectChangedEventArgs

> 表示业务对象属性更改或集合更改事件的参数。该类包含有关更改的对象、属性更改事件、集合更改类型和集合索引的信息。

- **Type**: class
- **Package**: `com.euonia.osba`
- **Author**: damon(zhaorong@outlook.com)

## Constructors

### ObjectChangedEventArgs

- **Parameters**:
  - `changedObject` (`Object`): 发生更改的对象

### ObjectChangedEventArgs

- **Parameters**:
  - `changedObject` (`Object`): 发生更改的对象
  - `propertyChangedEvent` (`PropertyChangeEvent`): 属性变更事件
  - `collectionChangeType` (`CollectionChangeType`): 集合变更类型
  - `collectionIndex` (`int`): 集合索引

## Methods

### getChangedObject

- **Returns**: `Object` — 发生更改的对象

### getPropertyChangedEvent

- **Returns**: `PropertyChangeEvent` — 属性变更事件

### getCollectionChangeType

- **Returns**: `CollectionChangeType` — 集合变更类型

### getCollectionIndex

- **Returns**: `int` — 集合索引

## Inner Enums

### CollectionChangeType

> 集合变更类型枚举。

| Constant | Description |
|----------|-------------|
| `ADD` | 添加元素 |
| `REMOVE` | 移除元素 |
| `REPLACE` | 替换元素 |
| `CLEAR` | 清空集合 |
