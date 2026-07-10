# Range

> 用于指定数值范围的注解。可应用于字段或方法参数，表示该数值必须在指定的最小值和最大值之间。
>
> 该注解支持以下属性：
> - `min`：指定允许的最小值，默认为 `Double.MIN_VALUE`。
> - `max`：指定允许的最大值，默认为 `Double.MAX_VALUE`。
> - `inclusiveMin`：是否包含最小值，默认为 `false`。
> - `inclusiveMax`：是否包含最大值，默认为 `false`。

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
| `min()` | `double` | `Double.MIN_VALUE` | 指定允许的最小值。 |
| `max()` | `double` | `Double.MAX_VALUE` | 指定允许的最大值。 |
| `inclusiveMin()` | `boolean` | `false` | 是否包含最小值。为 `true` 时允许指定值等于最小值。 |
| `inclusiveMax()` | `boolean` | `false` | 是否包含最大值。为 `true` 时允许指定值等于最大值。 |
| `message()` | `String` | `""` | 自定义验证失败时的错误消息。默认为空字符串。 |

## Usage

```java
// 字段级：限制 age 在 1 ~ 150（含边界）
@Range(min = 1, max = 150, inclusiveMin = true, inclusiveMax = true)
private int age;

// 参数级：限制 score 在 0 ~ 100（不含边界）
public void setScore(@Range(min = 0, max = 100) double score) {
    this.score = score;
}

// 仅指定最小值
@Range(min = 1)
private long positiveNumber;

// 自定义错误消息
@Range(min = 18, max = 60, message = "年龄必须在18到60之间")
private int adultAge;
```
