# RequiredValidator

> RequiredValidator 是一个用于验证对象是否满足 Required 注解约束的验证器类。
> 它实现了 Validator 接口，并提供了 validate 方法来执行验证逻辑。
>
> 验证逻辑如下：
> - 如果值为 null，则验证失败，并返回指定的错误消息或默认消息 `"Value is required"`。
> - 如果值是一个空字符串且 allowEmpty 为 false，则验证失败，并返回指定的错误消息或默认消息 `"Value must not be empty"`。
> - 如果值不为 null 且不为空字符串（当 allowEmpty 为 false 时），则验证成功。

- **Module**: `core`
- **Type**: `final class`
- **Package**: `com.euonia.annotation`
- **Implements**: [`Validator`](./com.euonia.annotation.Validator.md)&lt;[`Required`](./com.euonia.annotation.Required.md)&gt;
- **Author**: damon(zhaorong@outlook.com)

## Annotations

### `@Override`

> 表示该方法重写了父接口 `Validator` 中定义的 validate 方法。

## Methods

### validate

> 执行验证逻辑：如果值为 null，验证失败，返回 `"Value is required"`。如果值为空字符串且 allowEmpty 为 false，验证失败，返回 `"Value must not be empty"`。否则验证成功。

- **Parameters**:
  - `annotation` ([`Required`](./com.euonia.annotation.Required.md)): 要验证的注解实例
  - `value` (`Object`): 要验证的值
- **Returns**: [`Result`](./com.euonia.annotation.Validator.md#result) - 验证结果，其中 `result` 表示验证是否通过，`message` 为验证失败时的错误消息
- **Throws**: （无）

## Usage

```java
// 创建验证器实例
RequiredValidator validator = new RequiredValidator();

// 假设 name 字段上有 @Required
// Required annotation = ...;

// 验证必填字段
Validator.Result r1 = validator.validate(annotation, "Alice");    // r1.result() == true
Validator.Result r2 = validator.validate(annotation, null);       // r2.result() == false, message: "Value is required"
Validator.Result r3 = validator.validate(annotation, "");        // r3.result() == false, message: "Value must not be empty"
```
