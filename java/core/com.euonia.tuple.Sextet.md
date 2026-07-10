# Sextet

> 表示包含六个值的元组，这些值可以是不同类型。此类是不可变的。

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
| `V3` | *(无)* | 第三个值的类型 |
| `V4` | *(无)* | 第四个值的类型 |
| `V5` | *(无)* | 第五个值的类型 |
| `V6` | *(无)* | 第六个值的类型 |

## Record Components

| Component | Type | Description |
|-----------|------|-------------|
| `value1` | `V1` | 元组的第一个值 |
| `value2` | `V2` | 元组的第二个值 |
| `value3` | `V3` | 元组的第三个值 |
| `value4` | `V4` | 元组的第四个值 |
| `value5` | `V5` | 元组的第五个值 |
| `value6` | `V6` | 元组的第六个值 |

## Methods

### of

> 使用指定值创建一个新的 Sextet 实例。

- **Parameters**:
  - `value1` (`V1`): 第一个值
  - `value2` (`V2`): 第二个值
  - `value3` (`V3`): 第三个值
  - `value4` (`V4`): 第四个值
  - `value5` (`V5`): 第五个值
  - `value6` (`V6`): 第六个值
- **Returns**: `Sextet<V1, V2, V3, V4, V5, V6>` - 新的 Sextet 实例

### from

> 从指定数组创建一个新的 Sextet 实例。

- **Parameters**:
  - `values` (`X[]`): 值数组
- **Returns**: `Sextet<X, X, X, X, X, X>` - 新的 Sextet 实例

### from

> 从指定列表创建一个新的 Sextet 实例。

- **Parameters**:
  - `values` (`List<X>`): 值列表
- **Returns**: `Sextet<X, X, X, X, X, X>` - 新的 Sextet 实例

### empty

> 创建一个所有值均为 null 的新 Sextet 实例。

- **Returns**: `Sextet<V1, V2, V3, V4, V5, V6>` - 空 Sextet 实例
