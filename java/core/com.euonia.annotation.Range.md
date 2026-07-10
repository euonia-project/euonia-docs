# Range

> 用于指定数值范围的注解。可应用于字段或方法参数，表示该数值必须在指定的最小值和最大值之间。
>
> 该注解支持两种方式指定范围：
> - **区间表达式**：通过 `value` 属性指定，如 `"[1,10]"`、`"(1,10]"`，此时忽略 `min`/`max`/`minBoundary`/`maxBoundary`。
> - **显式属性**：通过 `min`/`max`/`minBoundary`/`maxBoundary` 分别指定。

- **Module**: `core`
- **Type**: `annotation`
- **Package**: `com.euonia.annotation`
- **Retention**: `RetentionPolicy.RUNTIME`
- **Target**: `FIELD`, `PARAMETER`
- **Author**: damon(zhaorong@outlook.com)

## Inheritance

- 隐式继承 `java.lang.annotation.Annotation`

## Annotations

| Annotation | Element | Value | Description |
|-----------|---------|-------|-------------|
| `@Retention` | `value` | `RetentionPolicy.RUNTIME` | 保留策略为运行时 |
| `@Target` | `value` | `{FIELD, PARAMETER}` | 可用于字段和方法参数 |
| `@Validation` | `validator` | [`RangeValidator.class`](./com.euonia.annotation.RangeValidator.md) | 关联的验证器实现 |

## Elements

| Element | Type | Default | Description |
|---------|------|---------|-------------|
| `value()` | `String` | `""` | 指定值范围的区间表达式，例如 `"[1,10]"`、`"(1,10)"`、`"(1,10]"` 等。如果指定了区间表达式则忽略 min、max、minBoundary 和 maxBoundary 属性。 |
| `min()` | `double` | `Double.MIN_VALUE` | 指定允许的最小值。 |
| `max()` | `double` | `Double.MAX_VALUE` | 指定允许的最大值。 |
| `minBoundary()` | `Boundary` | `EXCLUSIVE` | 指定最小值的边界类型。 |
| `maxBoundary()` | `Boundary` | `EXCLUSIVE` | 指定最大值的边界类型。 |
| `message()` | `String` | `""` | 自定义验证失败时的错误消息。默认为空字符串。 |

## Inner Types

### Boundary

> 枚举类型，表示范围的边界类型。

- **Type**: `enum`

| Constant | Description |
|----------|-------------|
| `INCLUSIVE` | 包含边界值 |
| `EXCLUSIVE` | 不包含边界值 |

## Usage

```java
// 方式一：区间表达式（推荐，简洁直观）
@Range("[1, 150]")        // 1 ≤ x ≤ 150（两端包含）
private int age;

@Range("(0, 100)")        // 0 < x < 100（两端不包含）
private double score;

@Range("(0, 100]")        // 0 < x ≤ 100（左开右闭）
private double amount;

// 方式二：显式属性
@Range(min = 1, max = 150, minBoundary = Boundary.INCLUSIVE, maxBoundary = Boundary.INCLUSIVE)
private int age;

// 仅指定最小值
@Range("[1,]")
private long positiveNumber;

// 仅指定最大值
@Range("[,100]")
private long maxValue;

// 自定义错误消息
@Range(value = "[18, 60]", message = "年龄必须在18到60之间")
private int adultAge;
```
