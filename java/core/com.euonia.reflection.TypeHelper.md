# TypeHelper

> TypeHelper 是一个工具类，提供将值强制转换为目标类型的方法，支持原始类型、枚举、日期/时间转换、集合等。旨在简化类型转换并确保各种场景下的类型安全。

- **Module**: `core`
- **Type**: `final class`
- **Package**: `com.euonia.reflection`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### coerceValue

> 将给定的值强制转换为指定的目标类型。

- **Parameters**:
  - `desiredType` (`Class<?>`): 目标类型
  - `valueType` (`Class<?>`): 值的实际类型（可选，如果为 null 则使用 value 的运行时类型）
  - `value` (`Object`): 要转换的值
- **Returns**: `Object` - 转换后的值

### coerceValue

> 重载方法：当 valueType 不可用时，直接使用 value 的运行时类型进行转换。

- **Parameters**:
  - `desiredType` (`Class<T>`): 目标类型
  - `value` (`Object`): 要转换的值
- **Returns**: `T` - 转换后的值

### isPrimitiveOrWrapper

> 判断给定的类是否为原始类型、包装类型或 String。

- **Parameters**:
  - `clazz` (`Class<?>`): 要检查的类
- **Returns**: `boolean` - 如果是原始类型、包装类型或 String 则返回 true

### boxIfPrimitive

> 如果给定的类是原始类型，则返回其包装类型；否则返回该类本身。

- **Parameters**:
  - `type` (`Class<?>`): 要检查的类
- **Returns**: `Class<?>` - 如果是原始类型则返回包装类型，否则返回该类本身

### isPrimitiveNumber

> 检查给定的类是否是原始数字类型。

- **Parameters**:
  - `type` (`Class<?>`): 要检查的类
- **Returns**: `boolean` - 如果是原始数字类型则返回 true
