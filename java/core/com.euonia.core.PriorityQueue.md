# PriorityQueue

> PriorityQueue 是一个基于 Java 内置优先级队列实现的通用优先级队列类。
> 它使用 Pair 类来存储元素和其对应的优先级，并通过 Comparator 来确保队列按照优先级排序。
> 该类提供了基本的队列操作方法，如添加元素、检索和移除最高优先级元素、查看队列头部元素、清空队列、获取队列大小以及检查队列是否为空。

- **Module**: `core`
- **Type**: `class`
- **Package**: `com.euonia.core`
- **Author**: damon(zhaorong@outlook.com)

## Type Parameters

| Parameter | Bound | Description |
|-----------|-------|-------------|
| `E` | *(无)* | 元素类型 |
| `K` | `extends Comparable<K>` | 优先级类型，必须实现 Comparable 接口 |

## Methods

### PriorityQueue (constructor)

> 创建一个新的 PriorityQueue。

### add

> 将指定元素以给定的优先级插入此优先级队列。

- **Parameters**:
  - `value` (`E`): 要添加的元素
  - `priority` (`K`): 元素的优先级

### poll

> 检索并移除队列头部元素，如果队列为空则返回 null。

- **Returns**: `E` - 最高优先级元素的值，如果队列为空则返回 null

### peek

> 检索但不移除队列头部元素。

- **Returns**: `E` - 最高优先级元素的值，如果队列为空则返回 null

### clear

> 从队列中移除所有元素。

### size

> 返回队列中的元素数量。

- **Returns**: `int` - 队列中的元素数量

### isEmpty

> 检查队列是否为空。

- **Returns**: `boolean` - 如果队列为空则返回 true，否则返回 false
