# RegularRule

> RegularRule 类实现了一个基于正则表达式的验证规则，用于验证业务对象的字符串属性是否符合指定的正则表达式模式。
> 该规则允许配置是否忽略空值，并提供了一个消息工厂函数，用于根据属性值生成适当的错误消息。

- **Type**: class
- **Package**: `com.euonia.osba.rules`
- **Author**: damon(zhaorong@outlook.com)
- **Extends**: `RuleBase`

## Constructors

### `RegularRule(PropertyInfo<String> property)`
> 使用指定属性创建 RegularRule 实例。

**Parameters:**
- `property` (`PropertyInfo<String>`): 需要验证的属性

### `RegularRule(PropertyInfo<String> property, String expression, String message)`
> 使用指定的属性、正则表达式和错误消息创建 RegularRule 类的新实例。

**Parameters:**
- `property` (`PropertyInfo<String>`): 需要验证的属性
- `expression` (`String`): 正则表达式模式
- `message` (`String`): 错误消息

### `RegularRule(PropertyInfo<String> property, String expression, Function<String, String> messageFactory)`
> 使用指定的属性、正则表达式和消息工厂函数创建 RegularRule 类的新实例。

**Parameters:**
- `property` (`PropertyInfo<String>`): 需要验证的属性
- `expression` (`String`): 正则表达式模式
- `messageFactory` (`Function<String, String>`): 消息工厂函数，根据属性值生成适当的错误消息

## Methods

### `getExpression(): String`
> 获取正则表达式。

**Returns:** `String` — 正则表达式

### `isIgnoreNullValue(): boolean`
> 是否忽略空值。

**Returns:** `boolean` — 是否忽略空值

### `setIgnoreNullValue(boolean ignoreNullValue): void`
> 设置是否忽略空值。

**Parameters:**
- `ignoreNullValue` (`boolean`): 是否忽略空值

### `execute(RuleContext context): void`
> 执行规则的验证逻辑，检查目标对象是否为业务对象，检索属性值，并根据配置的正则表达式验证该值。如果验证失败，则将带有适当消息的错误结果添加到上下文中。

**Parameters:**
- `context` (`RuleContext`): 规则上下文，包含有关规则执行环境的信息，如目标对象和属性值。

### `expression(String expression): RegularRule`
> 设置正则表达式。

**Parameters:**
- `expression` (`String`): 正则表达式模式

**Returns:** `RegularRule` — 当前 RegularRule 实例，以便进行链式调用

### `message(Function<String, String> messageFactory): RegularRule`
> 设置消息工厂函数，根据属性值生成适当的错误消息。

**Parameters:**
- `messageFactory` (`Function<String, String>`): 消息工厂函数

**Returns:** `RegularRule` — 当前 RegularRule 实例，以便进行链式调用

### `message(String message): RegularRule`
> 设置静态错误消息。

**Parameters:**
- `message` (`String`): 错误消息

**Returns:** `RegularRule` — 当前 RegularRule 实例，以便进行链式调用

### `ignoreNullValue(boolean ignoreNullValue): RegularRule`
> 设置是否忽略空值。

**Parameters:**
- `ignoreNullValue` (`boolean`): 是否忽略空值

**Returns:** `RegularRule` — 当前 RegularRule 实例，以便进行链式调用

## Static Methods

### `of(PropertyInfo<String> property): RegularRule`
> 创建一个新的 RegularRule 实例，绑定到指定的属性。

**Parameters:**
- `property` (`PropertyInfo<String>`): 要验证的属性信息

**Returns:** `RegularRule` — 一个新的 RegularRule 实例
