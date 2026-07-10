# Septet

> 表示包含七个值的元组，这些值可以是不同类型。此类是不可变的。

- **Type**: record
- **Package**: `com.euonia.tuple`
- **Author**: damon(zhaorong@outlook.com)

## Record Components

| Component | Type | Description |
|-----------|------|-------------|
| `value1` | `V1` | 元组的第一个值 |
| `value2` | `V2` | 元组的第二个值 |
| `value3` | `V3` | 元组的第三个值 |
| `value4` | `V4` | 元组的第四个值 |
| `value5` | `V5` | 元组的第五个值 |
| `value6` | `V6` | 元组的第六个值 |
| `value7` | `V7` | 元组的第七个值 |

## Methods

### of

> 使用指定值创建一个新的 Septet 实例。

- **Parameters**:
  - `value1` (`V1`): 第一个值
  - `value2` (`V2`): 第二个值
  - `value3` (`V3`): 第三个值
  - `value4` (`V4`): 第四个值
  - `value5` (`V5`): 第五个值
  - `value6` (`V6`): 第六个值
  - `value7` (`V7`): 第七个值
- **Returns**: `Septet<V1, V2, V3, V4, V5, V6, V7>` - 新的 Septet 实例

### from

> 从指定数组创建一个新的 Septet 实例。

- **Parameters**:
  - `values` (`X[]`): 值数组
- **Returns**: `Septet<X, X, X, X, X, X, X>` - 新的 Septet 实例

### from

> 从指定列表创建一个新的 Septet 实例。

- **Parameters**:
  - `values` (`List<X>`): 值列表
- **Returns**: `Septet<X, X, X, X, X, X, X>` - 新的 Septet 实例

### empty

> 创建一个所有值均为 null 的新 Septet 实例。

- **Returns**: `Septet<V1, V2, V3, V4, V5, V6, V7>` - 空 Septet 实例
