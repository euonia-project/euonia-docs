# LambdaRule

> LambdaRule 允许使用 lambda 函数定义验证规则，为实现业务对象特定属性的自定义验证逻辑提供了灵活性。

- **Type**: class
- **Package**: `com.euonia.osba.rules`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<T>` — 被验证的属性值的类型
- **Extends**: `RuleBase`

## Constructors

### `LambdaRule(PropertyInfo<T> property)`
> 使用指定属性创建 LambdaRule 实例。

**Parameters:**
- `property` (`PropertyInfo<T>`): 要验证的属性信息

### `LambdaRule(PropertyInfo<T> property, BiFunction<T, RuleContext, Boolean> function, String message)`
> 使用指定属性、验证函数和静态错误消息创建 LambdaRule 实例。

**Parameters:**
- `property` (`PropertyInfo<T>`): 要验证的属性信息
- `function` (`BiFunction<T, RuleContext, Boolean>`): 验证函数，接受属性值和规则上下文，返回布尔值指示验证是否通过
- `message` (`String`): 验证失败时的静态错误消息

### `LambdaRule(PropertyInfo<T> property, BiFunction<T, RuleContext, Boolean> function, Function<T, String> messageFactory)`
> 使用指定属性、验证函数和消息工厂创建 LambdaRule 实例。

**Parameters:**
- `property` (`PropertyInfo<T>`): 要验证的属性信息
- `function` (`BiFunction<T, RuleContext, Boolean>`): 验证函数，接受属性值和规则上下文，返回布尔值指示验证是否通过
- `messageFactory` (`Function<T, String>`): 消息工厂，根据属性值生成错误消息

## Methods

### `execute(RuleContext context): void`
> 执行规则的验证逻辑，检查目标对象是否为业务对象，检索属性值，并使用提供的 lambda 函数验证该值。如果验证失败，则将带有适当消息的错误结果添加到上下文中。

**Parameters:**
- `context` (`RuleContext`): 规则上下文，包含有关规则执行环境的信息，如目标对象和属性值。

### `check(BiFunction<T, RuleContext, Boolean> function): LambdaRule<T>`
> 设置验证规则的逻辑函数。该方法接受一个 BiFunction，允许在验证过程中访问被验证的属性值和规则上下文。函数应返回一个布尔值，指示验证是否通过。

**Parameters:**
- `function` (`BiFunction<T, RuleContext, Boolean>`): 一个 BiFunction，接受属性值和规则上下文，返回布尔值

**Returns:** `LambdaRule<T>` — 当前 LambdaRule 实例，以便进行链式调用

### `message(Function<T, String> messageFactory): LambdaRule<T>`
> 设置验证失败时的错误消息生成器。该方法接受一个 lambda 函数，该函数根据被验证的属性值生成错误消息。这样可以根据不同的属性值动态生成适当的错误消息。

**Parameters:**
- `messageFactory` (`Function<T, String>`): 一个函数，接受属性值并返回错误消息字符串

**Returns:** `LambdaRule<T>` — 当前 LambdaRule 实例，以便进行链式调用

### `message(String message): LambdaRule<T>`
> 设置验证失败时的静态错误消息。

**Parameters:**
- `message` (`String`): 静态错误消息

**Returns:** `LambdaRule<T>` — 当前 LambdaRule 实例，以便进行链式调用

## Static Methods

### `of(PropertyInfo<T> property): LambdaRule<T>`
> 创建一个新的 LambdaRule 实例，绑定到指定的属性。

**Type Parameters:**
- `<T>`: 属性的类型

**Parameters:**
- `property` (`PropertyInfo<T>`): 要验证的属性信息

**Returns:** `LambdaRule<T>` — 一个新的 LambdaRule 实例
