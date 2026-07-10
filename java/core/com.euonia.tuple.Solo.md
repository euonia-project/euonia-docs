# Solo

> 表示包含单个值的元组，该值可以是任意类型。此类是不可变的。

- **Type**: record
- **Package**: `com.euonia.tuple`
- **Author**: damon(zhaorong@outlook.com)

## Record Components

| Component | Type | Description |
|-----------|------|-------------|
| `value` | `V` | 元组的值 |

## Methods

### of

> 使用指定值创建一个新的 Solo 实例。

- **Parameters**:
  - `value` (`V`): 元组的值
- **Returns**: `Solo<V>` - 新的 Solo 实例

### from

> 从指定数组创建一个新的 Solo 实例。

- **Parameters**:
  - `values` (`X[]`): 值数组
- **Returns**: `Solo<X>` - 新的 Solo 实例

### from

> 从指定列表创建一个新的 Solo 实例。

- **Parameters**:
  - `values` (`List<X>`): 值列表
- **Returns**: `Solo<X>` - 新的 Solo 实例

### empty

> 创建一个所有值均为 null 的新 Solo 实例。

- **Returns**: `Solo<V>` - 空 Solo 实例
