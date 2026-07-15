# ArgumentNullException

> 参数空值异常类，提供静态守卫方法用于检查方法参数是否为 null 或空。当参数不满足条件时抛出此异常。继承自 `IllegalArgumentException`。

- **Module**: `core`
- **Type**: `class`
- **Package**: `com.euonia.core`
- **Extends**: `IllegalArgumentException`
- **Author**: damon(zhaorong@outlook.com)

## Constructors

### ArgumentNullException

> 使用指定的详细消息构造异常。

- **Parameters**:
  - `message` (`String`): 异常的详细消息

## Static Methods

### throwIfNull

> 检查参数是否为 null，如果是则抛出 ArgumentNullException。

- **Parameters**:
  - `argument` (`Object`): 要检查的参数
  - `param` (`String`): 参数名称
- **Throws**: `ArgumentNullException` - 如果参数为 null

### throwIfNull

> 检查参数是否为 null，使用 Supplier 延迟生成错误消息。

- **Parameters**:
  - `argument` (`Object`): 要检查的参数
  - `message` (`Supplier<String>`): 异常消息的提供者
- **Throws**: `ArgumentNullException` - 如果参数为 null

### throwIfNullOrEmpty

> 检查字符串是否为 null 或空，如果是则抛出 ArgumentNullException。

- **Parameters**:
  - `argument` (`String`): 要检查的字符串
  - `param` (`String`): 参数名称
- **Throws**: `ArgumentNullException` - 如果字符串为 null 或空

### throwIfNullOrEmpty

> 检查数组是否为 null 或空，如果是则抛出 ArgumentNullException。

- **Type Parameters**:
  - `T`: 数组元素类型
- **Parameters**:
  - `argument` (`T[]`): 要检查的数组
  - `param` (`String`): 参数名称
- **Throws**: `ArgumentNullException` - 如果数组为 null 或空

### throwIfNullOrEmpty

> 检查 List 是否为 null 或空，如果是则抛出 ArgumentNullException。

- **Type Parameters**:
  - `T`: List 元素类型
- **Parameters**:
  - `argument` (`List<T>`): 要检查的 List
  - `param` (`String`): 参数名称
- **Throws**: `ArgumentNullException` - 如果 List 为 null 或空

### throwIfNullOrEmpty

> 检查 Collection 是否为 null 或空，如果是则抛出 ArgumentNullException。

- **Type Parameters**:
  - `T`: 集合元素类型
- **Parameters**:
  - `argument` (`Collection<T>`): 要检查的集合
  - `param` (`String`): 参数名称
- **Throws**: `ArgumentNullException` - 如果集合为 null 或空

### throwIfNullOrEmpty

> 检查 Map 是否为 null 或空，如果是则抛出 ArgumentNullException。

- **Type Parameters**:
  - `K`: Map 键类型
  - `V`: Map 值类型
- **Parameters**:
  - `argument` (`Map<K, V>`): 要检查的 Map
  - `param` (`String`): 参数名称
- **Throws**: `ArgumentNullException` - 如果 Map 为 null 或空

## Usage

```java
// 基本用法 - 使用参数名
ArgumentNullException.throwIfNull(user, "user");
ArgumentNullException.throwIfNullOrEmpty(name, "name");

// 延迟消息（Supplier 形式）
ArgumentNullException.throwIfNull(config, () -> "配置对象不能为空");

// 支持多种集合类型
ArgumentNullException.throwIfNullOrEmpty(list, "list");
ArgumentNullException.throwIfNullOrEmpty(map, "map");
ArgumentNullException.throwIfNullOrEmpty(array, "array");
```
