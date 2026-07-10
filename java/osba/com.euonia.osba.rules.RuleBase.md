# RuleBase

> 提供规则的基础实现，包括公共属性和方法。此类可被扩展以创建具体的规则实现。

- **Type**: abstract class
- **Package**: `com.euonia.osba.rules`
- **Author**: damon(zhaorong@outlook.com)
- **Implements**: `Rule`

## Constructors

### RuleBase

> 使用默认名称创建 RuleBase 类的新实例。名称将基于规则类的类型自动生成。

### RuleBase

> 使用指定属性创建 RuleBase 类的新实例。名称将基于规则类的类型和属性名称自动生成。

- **Parameters**:
  - `property` (`PropertyInfo<?>`): 与规则关联的属性

### RuleBase

> 使用指定属性和成员创建 RuleBase 类的新实例。名称将基于规则类的类型、属性名称和成员名称自动生成。

- **Parameters**:
  - `property` (`PropertyInfo<?>`): 与规则关联的属性
  - `member` (`Member`): 与规则关联的成员，通常是一个方法或字段，用于提供额外的上下文信息以生成规则名称

### RuleBase

> 使用指定属性和名称创建 RuleBase 类的新实例。名称将基于规则类的类型、属性名称和提供的名称自动生成。

- **Parameters**:
  - `property` (`PropertyInfo<?>`): 与规则关联的属性
  - `names` (`String...`): 提供的名称，用于生成规则名称

## Methods

### getName

> 获取规则的名称，通常基于规则类的类型和相关属性生成。名称用于唯一标识规则并提供上下文信息。格式为 `rule://{typeName}/{name1}/{name2}/...`

- **Returns**: `String` — 规则的名称

### getProperty

> 获取与规则关联的属性信息。此属性提供了规则应用的上下文，通常用于确定规则适用的对象属性。

- **Returns**: `PropertyInfo<?>` — 与规则关联的属性信息

### getPriority

> 获取规则的优先级。优先级用于确定在多个规则适用时的执行顺序。默认实现返回 0，表示中等优先级。子类可以覆盖此方法以提供不同的优先级值。

- **Returns**: `int` — 规则的优先级
