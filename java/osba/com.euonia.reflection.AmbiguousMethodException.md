# AmbiguousMethodException

> AmbiguousMethodException 是一个自定义异常，当多个方法匹配工厂方法的条件时抛出，导致无法明确应使用哪个方法。它继承自 RuntimeException，并提供描述方法选择过程中歧义的消息。此异常通常在存在多个同名或同注解的方法都可能是工厂方法，且提供的条件无法清晰区分它们时抛出。

- **Type**: class
- **Package**: `com.euonia.reflection`
- **Author**: damon(zhaorong@outlook.com)
- **Extends**: `RuntimeException`

## Constructors

### AmbiguousMethodException

> 使用指定的消息构造一个新的 AmbiguousMethodException。

- **Parameters**:
  - `message` (`String`): 描述方法选择过程中歧义的消息

### AmbiguousMethodException

> 使用指定的消息和原因构造一个新的 AmbiguousMethodException。

- **Parameters**:
  - `message` (`String`): 描述方法选择过程中歧义的消息
  - `cause` (`Throwable`): 导致此异常的原因
