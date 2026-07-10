# RangeValidator

> RangeValidator 是一个用于验证数值是否在指定范围内的验证器类。
> 它实现了 Validator 接口，并提供了 validate 方法来执行验证逻辑。
>
> 验证逻辑如下：
> - 如果值是一个数字，则检查其是否在注解指定的最小值和最大值之间，并根据 inclusiveMin 和 inclusiveMax 属性判断是否包含边界值。
> - 如果数值不在指定范围内，则验证失败，并返回指定的错误消息或默认消息 `"Value must be between {min} and {max}{inclusiveMin}{inclusiveMax}"`。
> - 如果值不是数字，则验证成功。

- **Module**: `core`
- **Type**: `final class`
- **Package**: `com.euonia.annotation`
- **Implements**: [`Validator`](./com.euonia.annotation.Validator.md)&lt;[`Range`](./com.euonia.annotation.Range.md)&gt;
- **Author**: damon(zhaorong@outlook.com)

## Annotations

### `@Override`

> 表示该方法重写了父接口 `Validator` 中定义的 validate 方法。

## Methods

### validate

> 执行验证逻辑：如果值是一个数字，则检查其是否在注解指定的最小值和最大值之间，并根据 inclusiveMin 和 inclusiveMax 属性判断是否包含边界值。如果值不是数字，则验证成功。

- **Parameters**:
  - `annotation` ([`Range`](./com.euonia.annotation.Range.md)): 要验证的注解实例
  - `value` (`Object`): 要验证的值
- **Returns**: [`Result`](./com.euonia.annotation.Validator.md#result) - 验证结果，其中 `result` 表示验证是否通过，`message` 为验证失败时的错误消息
- **Throws**: （无）

## Usage

```java
// 创建验证器实例
RangeValidator validator = new RangeValidator();

// 定义一个范围注解 (需要实际创建或通过反射获取)
// 假设 age 字段上有 @Range(min = 1, max = 150, inclusiveMin = true)
// Range annotation = ...;

// 验证值是否在范围内
Validator.Result result = validator.validate(annotation, 25);   // result.result() == true
Validator.Result result2 = validator.validate(annotation, 200); // result.result() == false, message: "Value must be between 1.0 and 150.0 (inclusive) (inclusive)"
```
