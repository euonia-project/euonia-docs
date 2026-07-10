# StringLengthValidator

> StringLengthValidator 是一个用于验证字符串长度是否在指定范围内的验证器类。
> 它实现了 Validator 接口，并提供了 validate 方法来执行验证逻辑。
>
> 验证逻辑如下：
> - 如果值是一个字符串，则检查其长度是否在注解指定的最小值和最大值之间。
> - 如果长度不在指定范围内，则验证失败，并返回指定的错误消息或默认消息 `"Value must be between {min} and {max} characters long"`。
> - 如果值不是字符串，则验证成功。

- **Module**: `core`
- **Type**: `final class`
- **Package**: `com.euonia.annotation`
- **Implements**: [`Validator`](./com.euonia.annotation.Validator.md)&lt;[`StringLength`](./com.euonia.annotation.StringLength.md)&gt;
- **Author**: damon(zhaorong@outlook.com)

## Annotations

### `@Override`

> 表示该方法重写了父接口 `Validator` 中定义的 validate 方法。

## Methods

### validate

> 执行验证逻辑：如果值是一个字符串，则检查其长度是否在注解指定的最小值和最大值之间。如果长度不在指定范围内，返回失败结果。如果值不是字符串，则验证成功。

- **Parameters**:
  - `annotation` ([`StringLength`](./com.euonia.annotation.StringLength.md)): 要验证的注解实例
  - `value` (`Object`): 要验证的值
- **Returns**: [`Result`](./com.euonia.annotation.Validator.md#result) - 验证结果，其中 `result` 表示验证是否通过，`message` 为验证失败时的错误消息
- **Throws**: （无）

## Usage

```java
// 创建验证器实例
StringLengthValidator validator = new StringLengthValidator();

// 假设 name 字段上有 @StringLength(min = 2, max = 50)
// StringLength annotation = ...;

// 验证字符串长度
Validator.Result r1 = validator.validate(annotation, "Alice");  // r1.result() == true
Validator.Result r2 = validator.validate(annotation, "A");       // r2.result() == false, message: "Value must be between 2 and 50 characters long"

// 非字符串值直接通过
Validator.Result r3 = validator.validate(annotation, 123);  // r3.result() == true
```
