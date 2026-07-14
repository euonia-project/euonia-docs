# RequiredRule

> RequiredRule 类实现了一个验证规则，用于确保业务对象的特定属性具有非空值。
> 该规则检查属性值是否为 null 或空字符串，如果验证失败，则将带有适当消息的错误结果添加到上下文中。

- **Type**: class
- **Package**: `com.euonia.osba.rules`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<T>`
- **Extends**: `RuleBase`

## Constructors

### `RequiredRule(PropertyInfo<T> property, String message)`
> 使用指定的属性和错误消息创建 RequiredRule 类的新实例。

**Parameters:**
- `property` (`PropertyInfo<T>`): 需要验证的属性
- `message` (`String`): 错误消息

### `RequiredRule(PropertyInfo<T> property, Function<Object, String> messageFactory)`
> 使用指定的属性和消息工厂函数创建 RequiredRule 类的新实例。

**Parameters:**
- `property` (`PropertyInfo<T>`): 需要验证的属性
- `messageFactory` (`Function<Object, String>`): 消息工厂函数，根据属性值生成适当的错误消息

## Methods

### `execute(RuleContext context): void`
> 执行规则的验证逻辑，检查目标对象是否为业务对象，检索属性值，并验证该值是否为 null 或空字符串。如果验证失败，则将带有适当消息的错误结果添加到上下文中。

**Parameters:**
- `context` (`RuleContext`): 规则上下文，包含有关规则执行环境的信息，如目标对象和属性值。

### `message(String message): RequiredRule<T>`
> 设置自定义的错误消息字符串，用于在验证失败时返回给用户。

**Parameters:**
- `message` (`String`): 自定义的错误消息字符串

**Returns:** `RequiredRule<T>` — 当前的 RequiredRule 实例，以便进行链式调用

### `message(Function<Object, String> messageFactory): RequiredRule<T>`
> 设置自定义的消息工厂函数，用于根据属性值生成适当的错误消息。

**Parameters:**
- `messageFactory` (`Function<Object, String>`): 一个函数，接受属性值作为输入，并返回相应的错误消息字符串。

**Returns:** `RequiredRule<T>` — 当前的 RequiredRule 实例，以便进行链式调用。

## Static Methods

### `of(PropertyInfo<T> property): RequiredRule<T>`
> 创建一个新的 RequiredRule 实例，绑定到指定的属性。

**Type Parameters:**
- `<T>`: 属性的类型

**Parameters:**
- `property` (`PropertyInfo<T>`): 要验证的属性信息

**Returns:** `RequiredRule<T>` — 一个新的 RequiredRule 实例
