# MissingMethodException

> 方法缺失异常，当在给定类中找不到具有特定名称或注解的方法时抛出。提供有关未找到的类型和方法的相关信息。继承自 `RuntimeException`。

- **Module**: `core`
- **Type**: `class`
- **Package**: `com.euonia.reflection`
- **Extends**: `RuntimeException`
- **Author**: damon(zhaorong@outlook.com)

## Constructors

### MissingMethodException

> 使用指定的类型名称和方法名称构造异常。

- **Parameters**:
  - `typeName` (`String`): 预期找到该方法的类名称
  - `methodName` (`String`): 预期但未找到的方法名称或注解

## Methods

### getTypeName

> 返回预期找到该方法的类名称。

- **Returns**: `String` - 类名称

### getMethodName

> 返回预期但未找到的方法名称或注解。

- **Returns**: `String` - 方法名称或注解
