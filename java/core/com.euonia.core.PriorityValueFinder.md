# PriorityValueFinder

> 用于在优先级队列中根据过滤谓词查找值的工具类。提供方法在优先级队列中搜索并返回第一个匹配给定过滤条件的值。如果未找到匹配值，则返回指定的默认值。

- **Type**: class
- **Package**: `com.euonia.core`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### find

> 在优先级队列中查找第一个匹配给定过滤条件的值。如果未找到匹配值，则返回默认值。

- **Parameters**:
  - `values` (`PriorityQueue<Supplier<T>, Integer>`): 要搜索的优先级队列
  - `filter` (`Predicate<T>`): 应用于每个值的过滤谓词
  - `defaultValue` (`T`): 未找到匹配值时返回的默认值
- **Returns**: `T` - 第一个匹配的值，如果未找到则返回默认值

### find

> 在由 consumer 提供的优先级队列中查找第一个匹配给定过滤条件的值。如果未找到匹配值，则返回默认值。

- **Parameters**:
  - `queueConsumer` (`Consumer<PriorityQueue<Supplier<T>, Integer>>`): 提供要搜索的优先级队列的 consumer
  - `filter` (`Predicate<T>`): 应用于每个值的过滤谓词
  - `defaultValue` (`T`): 未找到匹配值时返回的默认值
- **Returns**: `T` - 第一个匹配的值，如果未找到则返回默认值
