# Tuple

> 表示一个有序的值集合，其中每个值可以是任意类型。元组是不可变的，可以包含重复值。提供了访问值、检查值是否存在以及执行常见元组操作的方法。`Tuple` 接口继承 `Iterable<Object>` 和 `Serializable`。

- **Module**: `core`
- **Type**: `interface`
- **Package**: `com.euonia.tuple`
- **Extends**: `Iterable<Object>`, `Serializable`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### size

> 返回元组中值的数量。

- **Returns**: `int` - 元组中值的数量

### value

> 返回元组中指定索引位置的值。

- **Parameters**:
  - `index` (`int`): 要返回的值的索引
- **Returns**: `Object` - 指定索引位置的值
- **Throws**: `IndexOutOfBoundsException` - 如果索引超出范围

### values

> 返回包含元组中所有值的列表。

- **Returns**: `List<Object>` - 包含元组中所有值的列表

### contains

> 检查元组是否包含指定的值。

- **Parameters**:
  - `value` (`Object`): 要检查的值
- **Returns**: `boolean` - 如果元组包含该值则返回 true

### containsAll

> 检查元组是否包含所有指定的值。

- **Parameters**:
  - `values` (`Collection<?>`): 要检查的值
- **Returns**: `boolean` - 如果元组包含所有值则返回 true

### containsAll

> 检查元组是否包含指定元组中的所有值。

- **Parameters**:
  - `tuple` (`Tuple`): 要检查其值的元组
- **Returns**: `boolean` - 如果元组包含指定元组中的所有值则返回 true
