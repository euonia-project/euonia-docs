# AmbiguousMethodException

> 方法歧义异常，当存在多个方法匹配工厂方法的条件时抛出，导致无法确定应使用哪个方法。继承自 `RuntimeException`。

- **Module**: `core`
- **Type**: `class`
- **Package**: `com.euonia.reflection`
- **Extends**: `RuntimeException`
- **Author**: damon(zhaorong@outlook.com)

## Constructors

### AmbiguousMethodException

> 使用默认消息构造异常。默认消息从国际化资源文件中获取。

### AmbiguousMethodException

> 使用指定的消息构造异常。

- **Parameters**:
  - `message` (`String`): 描述歧义情况的消息

### AmbiguousMethodException

> 使用指定的消息和原因构造异常。

- **Parameters**:
  - `message` (`String`): 描述歧义情况的消息
  - `cause` (`Throwable`): 导致此异常的原因
