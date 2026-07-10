# Duet

> 表示包含两个值的元组，这两个值可以是不同类型。此类是不可变的。

- **Module**: `core`
- **Type**: `record`
- **Package**: `com.euonia.tuple`
- **Implements**: [`Tuple`](./com.euonia.tuple.Tuple.md)
- **Author**: damon(zhaorong@outlook.com)

## Type Parameters

| Parameter | Bound | Description |
|-----------|-------|-------------|
| `V1` | *(无)* | 第一个值的类型 |
| `V2` | *(无)* | 第二个值的类型 |

## Record Components

| Component | Type | Description |
|-----------|------|-------------|
| `value1` | `V1` | 第一个值 |
| `value2` | `V2` | 第二个值 |

## Methods

### of

> 使用给定值创建一个新的 Duet 实例。

- **Parameters**:
  - `value1` (`V1`): 第一个值
  - `value2` (`V2`): 第二个值
- **Returns**: `Duet<V1, V2>` - 新的 Duet 实例

### from

> 从给定数组创建一个新的 Duet 实例。

- **Parameters**:
  - `values` (`X[]`): 值数组
- **Returns**: `Duet<X, X>` - 新的 Duet 实例

### from

> 从指定列表创建一个新的 Duet 实例。

- **Parameters**:
  - `values` (`List<X>`): 值列表
- **Returns**: `Duet<X, X>` - 新的 Duet 实例

### empty

> 创建一个所有值均为 null 的新 Duet 实例。

- **Returns**: `Duet<V1, V2>` - 空 Duet 实例
