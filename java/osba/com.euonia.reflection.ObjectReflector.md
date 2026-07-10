# ObjectReflector

> ObjectReflector 是一个工具类，提供了反射相关的方法，用于在运行时查找和匹配带有特定注解的方法。主要功能包括：findFactoryMethod（根据目标类型、注解类型和可选的参数，查找匹配的方法）、calculateParameterMatchScore（计算方法参数与给定参数之间的匹配度得分）、getCandidateMethods（获取所有符合条件的候选方法）、getParameterTypeName（生成参数类型名称的字符串表示）、getConventionMethodNames（根据注解类型生成符合命名约定的方法名称列表）。

- **Type**: class
- **Package**: `com.euonia.reflection`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### findFactoryMethod

> 查找带有特定注解的方法，并根据参数匹配度进行排序。使用缓存提高性能。

- **Parameters**:
  - `targetType` (`Class<T>`): 目标类型
  - `annotationType` (`Class<A>`): 注解类型
  - `criteria` (`Object[]`): 匹配条件
- **Returns**: `Method` — 匹配的方法
