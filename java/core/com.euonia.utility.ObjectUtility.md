# ObjectUtility

> 对象反射操作工具类，提供安全的方法查找和反射调用功能。所有方法都通过 Optional 优雅地处理方法不存在的情况，避免直接抛出异常。该类为抽象工具类，不可实例化。

- **Type**: `class`
- **Package**: `com.euonia.utility`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### getMethod

> 在指定的类中查找公共方法（包括继承的方法）。

- **Parameters**:
  - `clazz` (`Class<?>`): 要查找的类
  - `methodName` (`String`): 方法名
  - `parameterTypes` (`Class<?>...`): 方法参数类型
- **Returns**: `Optional<Method>` - 包含找到的方法的 Optional，如果未找到则为空

### getDeclaredMethod

> 在指定的类中查找已声明的方法（仅包括该类自身声明的方法，不包括继承的）。

- **Parameters**:
  - `clazz` (`Class<?>`): 要查找的类
  - `methodName` (`String`): 方法名
  - `parameterTypes` (`Class<?>...`): 方法参数类型
- **Returns**: `Optional<Method>` - 包含找到的方法的 Optional，如果未找到则为空

### invokeMethod

> 通过反射在指定对象上调用方法，参数类型从参数实例中自动推断。如果方法未找到或调用失败，返回 null。

- **Parameters**:
  - `obj` (`Object`): 要调用方法的对象
  - `methodName` (`String`): 方法名
  - `args` (`Object...`): 方法参数
- **Returns**: `Object` - 方法调用的返回值，如果方法不存在或调用失败则返回 null

### invokeMethod

> 通过反射在指定对象上调用方法，并将返回值强制转换为指定类型。如果方法未找到或调用失败，抛出异常。

- **Parameters**:
  - `returnType` (`Class<T>`): 期望的返回类型
  - `obj` (`Object`): 要调用方法的对象
  - `methodName` (`String`): 方法名
  - `args` (`Object...`): 方法参数
- **Returns**: `T` - 强制转换为指定类型的方法返回值
- **Throws**: `RuntimeException` - 如果方法不存在或调用失败
