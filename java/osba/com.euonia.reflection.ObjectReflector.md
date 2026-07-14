# ObjectReflector

> ObjectReflector 是一个工具类，提供了反射相关的方法，用于在运行时查找和匹配带有特定注解的方法。主要功能包括：findFactoryMethod — 根据目标类型、注解类型和可选的参数，查找匹配的方法。

- **Type**: final class
- **Package**: `com.euonia.reflection`
- **Author**: damon(zhaorong@outlook.com)

## Static Methods

### `findFactoryMethod(Class<T> targetType, Class<A> annotationType, Object[] criteria): Method`
> 查找带有特定注解的方法，并根据参数匹配度进行排序。

**Parameters:**
- `targetType` (`Class<T>`): 目标类型
- `annotationType` (`Class<A>`): 注解类型
- `criteria` (`Object[]`): 匹配条件

**Returns:** `Method` — 匹配的方法
