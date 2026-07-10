# SyntheticParameterizedType

> ParameterizedType 的可合成实现，允许在运行时手动构造参数化类型。当无法通过反射直接获取泛型类型信息时（如需要动态组合原始类型和类型参数），可使用该类创建合成的参数化类型实例。

- **Module**: `core`
- **Type**: `final class`
- **Package**: `com.euonia.reflection`
- **Implements**: `ParameterizedType`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### SyntheticParameterizedType (constructor)

> 使用指定的原始类型和类型参数构造合成参数化类型。

- **Parameters**:
  - `rawType` (`Type`): 原始类型
  - `typeArguments` (`Type...`): 类型参数

### getTypeName

> 返回类型的完整名称字符串，包含泛型参数。例如对于 `List<String>` 将返回 `"java.util.List<java.lang.String>"`。

- **Returns**: `String` - 包含泛型参数的类型名称

### getOwnerType

> 返回所有者类型。合成类型永远没有所有者，因此始终返回 null。

- **Returns**: `Type` - 始终为 null

### getRawType

> 返回此参数化类型的原始类型。

- **Returns**: `Type` - 原始类型

### getActualTypeArguments

> 返回此参数化类型的实际类型参数数组。

- **Returns**: `Type[]` - 类型参数数组
