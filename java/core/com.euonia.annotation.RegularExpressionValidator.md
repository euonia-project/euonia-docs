# RegularExpressionValidator

> RegularExpressionValidator 是一个用于验证对象是否满足 RegularExpression 注解约束的验证器类。
> 它实现了 Validator 接口，并提供了 validate 方法来执行验证逻辑。
>
> 验证逻辑如下：
> - 如果值是一个字符串，则检查该字符串是否匹配指定的正则表达式模式。
> - 如果字符串不匹配正则表达式，则验证失败，并返回指定的错误消息或默认消息 `"Value must match the regular expression: {pattern}"`。
> - 如果值不是字符串，则验证成功。

- **Module**: `core`
- **Type**: `final class`
- **Package**: `com.euonia.annotation`
- **Implements**: [`Validator`](./com.euonia.annotation.Validator.md)&lt;[`RegularExpression`](./com.euonia.annotation.RegularExpression.md)&gt;
- **Author**: damon(zhaorong@outlook.com)

## Annotations

### `@Override`

> 表示该方法重写了父接口 `Validator` 中定义的 validate 方法。

## Methods

### validate

> 执行验证逻辑：如果值是一个字符串，则检查该字符串是否匹配指定的正则表达式模式。如果字符串不匹配正则表达式，则验证失败，并返回指定的错误消息或默认消息。如果值不是字符串，则验证成功。

- **Parameters**:
  - `annotation` ([`RegularExpression`](./com.euonia.annotation.RegularExpression.md)): 要验证的注解实例
  - `value` (`Object`): 要验证的值
- **Returns**: [`Result`](./com.euonia.annotation.Validator.md#result) - 验证结果，其中 `result` 表示验证是否通过，`message` 为验证失败时的错误消息
- **Throws**: （无）

## Usage

```java
// 创建验证器实例
RegularExpressionValidator validator = new RegularExpressionValidator();

// 假设 email 字段上有 @RegularExpression("^[\\w.-]+@[\\w.-]+\\.[a-zA-Z]{2,}$")
// RegularExpression annotation = ...;

// 验证字符串是否匹配正则
Validator.Result r1 = validator.validate(annotation, "user@example.com");  // r1.result() == true
Validator.Result r2 = validator.validate(annotation, "invalid-email");      // r2.result() == false, message: "Value must match the regular expression: ^[\\w.-]+@[\\w.-]+\\.[a-zA-Z]{2,}$"

// 非字符串值直接通过
Validator.Result r3 = validator.validate(annotation, 123);  // r3.result() == true
```
