# Pair

> 一个表示键值对的记录类。键必须是可比较的，以确保可以基于键对键值对进行排序。

- **Module**: `core`
- **Type**: `record`
- **Package**: `com.euonia.core`
- **Author**: damon(zhaorong@outlook.com)

## Type Parameters

| Parameter | Bound | Description |
|-----------|-------|-------------|
| `K` | `extends Comparable<K>` | 键的类型 |
| `V` | *(无)* | 值的类型 |

## Record Components

| Component | Type | Description |
|-----------|------|-------------|
| `key` | `K` | 键值对的键 |
| `value` | `V` | 与键关联的值 |

## Methods

### of

> 创建一个新的 Pair 实例。键不能为空，否则将抛出 IllegalArgumentException。

- **Parameters**:
  - `key` (`K`): 键值对的键
  - `value` (`V`): 与键关联的值
- **Returns**: `Pair<K, V>` - 新的 Pair 实例
