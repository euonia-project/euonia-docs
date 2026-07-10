# Assert

> 参数断言工具类，提供常用的前置条件检查方法。当条件不满足时，抛出 `IllegalArgumentException`。

- **Module**: `core`
- **Type**: `class`
- **Package**: `com.euonia.utility`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### notNull

> 断言对象不为 null。

- **Parameters**:
  - `obj` (`Object`): 要检查的对象
  - `message` (`String`): 断言失败时的错误消息
- **Throws**: `IllegalArgumentException` - 如果对象为 null

### notNull

> 断言对象不为 null，使用 Supplier 延迟生成错误消息。

- **Parameters**:
  - `obj` (`Object`): 要检查的对象
  - `messageSupplier` (`Supplier<String>`): 断言失败时的错误消息提供者
- **Throws**: `IllegalArgumentException` - 如果对象为 null

### notEmpty

> 断言字符串不为空或空白。

- **Parameters**:
  - `str` (`String`): 要检查的字符串
  - `message` (`String`): 断言失败时的错误消息
- **Throws**: `IllegalArgumentException` - 如果字符串为 null、空或空白

### notEmpty

> 断言列表不为空。

- **Parameters**:
  - `list` (`List<?>`): 要检查的列表
  - `message` (`String`): 断言失败时的错误消息
- **Throws**: `IllegalArgumentException` - 如果列表为 null 或空

### notEmpty

> 断言数组不为空。

- **Parameters**:
  - `array` (`Object[]`): 要检查的数组
  - `message` (`String`): 断言失败时的错误消息
- **Throws**: `IllegalArgumentException` - 如果数组为 null 或空

### notContains

> 断言列表中不包含与给定断言匹配的任何元素。

- **Parameters**:
  - `list` (`List<T>`): 要检查的列表
  - `predicate` (`Predicate<T>`): 匹配断言
  - `message` (`String`): 断言失败时的错误消息
- **Throws**: `IllegalArgumentException` - 如果列表包含匹配断言元素

### notContains

> 断言数组中不包含与给定断言匹配的任何元素。

- **Parameters**:
  - `array` (`T[]`): 要检查的数组
  - `predicate` (`Predicate<T>`): 匹配断言
  - `message` (`String`): 断言失败时的错误消息
- **Throws**: `IllegalArgumentException` - 如果数组包含匹配断言元素
