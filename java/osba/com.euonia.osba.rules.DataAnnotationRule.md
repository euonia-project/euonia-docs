# DataAnnotationRule

> 表示一个基于应用于属性的特定注解的规则。
> 此类的目的是对其关联的属性值执行注解定义的验证逻辑。
> 该规则检查目标对象是否为业务对象，检索属性的值，然后使用注解指定的验证器来验证该值。
> 如果验证失败，则将带有适当消息的错误结果添加到上下文中。

- **Type**: class
- **Package**: `com.euonia.osba.rules`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<A extends Annotation>`
- **Extends**: `RuleBase`

## Constructors

### `DataAnnotationRule(PropertyInfo<?> property, A annotation, Class<?> validatorType)`
> 使用指定的属性和注解创建 DataAnnotationRule 类的新实例。

**Parameters:**
- `property` (`PropertyInfo<?>`): 与规则关联的属性
- `annotation` (`A`): 定义要应用的验证逻辑的注解
- `validatorType` (`Class<?>`): 将用于根据注解验证属性值的验证器类

## Methods

### `execute(RuleContext context): void`
> 执行规则的验证逻辑，检查目标对象是否为业务对象，检索属性值，并使用注解指定的验证器来验证该值。如果验证失败，则将带有适当消息的错误结果添加到上下文中。

**Parameters:**
- `context` (`RuleContext`): 规则上下文，包含有关规则执行环境的信息，如目标对象和属性值。
