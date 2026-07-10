# ValueObject

> 值对象的基类，提供了 {@code equals}、{@code hashCode} 和 {@code compareTo} 方法的实现。通过反射比较对象的所有声明字段。{@code compareTo} 按字段顺序比较，第一个不相等的字段决定排序结果；{@code equals} 要求所有字段相等；{@code hashCode} 使用交替乘数计算哈希值。

- **Type**: class
- **Package**: `com.euonia.domain`
- **Author**: damon(zhaorong@outlook.com)
- **Implements**: `Comparable<T>`

## Type Parameters

| Parameter | Bound | Description |
|-----------|-------|-------------|
| `T` | `ValueObject<T>` | 值对象的类型 |

## Methods

### compareTo

> 按字段顺序比较两个值对象。第一个不相等的字段决定排序结果；null 值在前，非 null 值在后。

- **Parameters**:
  - `other` (`T`): 要比较的另一个值对象
- **Returns**: `int` - 比较结果（负值表示小于，0 表示等于，正值表示大于）

### equals

> 比较两个值对象是否相等。要求所有字段相等才返回 true。

- **Parameters**:
  - `obj` (`T`): 要比较的值对象
- **Returns**: `boolean` - 如果所有字段相等则为 true

### hashCode

> 使用交替乘数（31、59、114）计算哈希值，确保不同字段组合产生不同的哈希。

- **Returns**: `int` - 基于所有字段计算的哈希值
