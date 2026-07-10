# RangeValidator

> RangeValidator 是一个用于验证数值是否在指定范围内的验证器类。
> 它实现了 Validator 接口，并提供了 validate 方法来执行验证逻辑。
>
> 验证逻辑如下：
> - 优先解析注解的 `value` 区间表达式（如 `"[1,10]"`），提取 min/max/boundary。
> - 如果 `value` 为空，则使用注解的 `min`/`max`/`minBoundary`/`maxBoundary` 属性。
> - 如果值是一个数字，则检查其是否在范围内，并根据 Boundary 判断是否包含边界值。
> - 如果数值不在指定范围内，则验证失败，并返回指定的错误消息或默认消息 `"Value must be between {min} and {max}{(inclusive)}"`。
> - 如果值不是数字，则验证成功。

- **Module**: `core`
- **Type**: `final class`
- **Package**: `com.euonia.annotation`
- **Implements**: [`Validator`](./com.euonia.annotation.Validator.md)&lt;[`Range`](./com.euonia.annotation.Range.md)&gt;
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `EXPRESSION` | `String` (static) | 区间表达式正则：`^(?<left>[\\[(])\\s*(?<min>...)\\s*,\\s*(?<max>...)\\s*(?<right>[\\])])$` |
| `pattern` | `Pattern` | 编译后的正则模式 |

## Annotations

### `@Override`

> 表示该方法重写了父接口 `Validator` 中定义的 validate 方法。

## Methods

### validate

> 执行验证逻辑：优先解析 `value` 区间表达式，fallback 到显式属性。检查数值是否在范围内并根据 Boundary 判断边界。

- **Parameters**:
  - `annotation` ([`Range`](./com.euonia.annotation.Range.md)): 要验证的注解实例
  - `value` (`Object`): 要验证的值
- **Returns**: [`Result`](./com.euonia.annotation.Validator.md#result) - 验证结果，其中 `result` 表示验证是否通过，`message` 为验证失败时的错误消息
- **Throws**: `IllegalArgumentException` - 如果 `value` 区间表达式格式无效

## Usage

```java
RangeValidator validator = new RangeValidator();

// 区间表达式方式
// @Range("[1, 150]") → 1 ≤ x ≤ 150
// Validator.Result r1 = validator.validate(annotation, 25);   // true
// Validator.Result r2 = validator.validate(annotation, 200);  // false

// 显式属性方式
// @Range(min = 0, max = 100, minBoundary = Boundary.EXCLUSIVE)
// Validator.Result r3 = validator.validate(annotation, 0);    // false (左边界不包含)
```
