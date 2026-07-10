# Trio

> 包含三个值的元组。此类是不可变的。

- **Type**: record
- **Package**: `com.euonia.tuple`
- **Author**: damon(zhaorong@outlook.com)

## Record Components

| Component | Type | Description |
|-----------|------|-------------|
| `value1` | `T1` | 元组的第一个值 |
| `value2` | `T2` | 元组的第二个值 |
| `value3` | `T3` | 元组的第三个值 |

## Methods

### of

> 使用指定值创建一个新的 Trio 实例。

- **Parameters**:
  - `value1` (`T1`): 第一个值
  - `value2` (`T2`): 第二个值
  - `value3` (`T3`): 第三个值
- **Returns**: `Trio<T1, T2, T3>` - 新的 Trio 实例

### from

> 从指定数组创建一个新的 Trio 实例。

- **Parameters**:
  - `values` (`X[]`): 值数组
- **Returns**: `Trio<X, X, X>` - 新的 Trio 实例

### from

> 从指定列表创建一个新的 Trio 实例。

- **Parameters**:
  - `values` (`List<X>`): 值列表
- **Returns**: `Trio<X, X, X>` - 新的 Trio 实例

### empty

> 创建一个所有值均为 null 的新 Trio 实例。

- **Returns**: `Trio<T1, T2, T3>` - 空 Trio 实例
