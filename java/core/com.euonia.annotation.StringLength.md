# StringLength

> 用于指定字符串长度范围的注解。可应用于字段或方法参数，表示该字符串的长度必须在指定的最小值和最大值之间。
>
> 该注解支持以下属性：
> - `min`：指定允许的最小长度，默认为 `0`。
> - `max`：指定允许的最大长度，默认为 `Integer.MAX_VALUE`。
> - `message`：自定义验证失败时的错误消息，默认为空字符串。

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
| `@Validation` | `validator` | [`StringLengthValidator.class`](./com.euonia.annotation.StringLengthValidator.md) | 关联的验证器实现 |

## Elements

| Element | Type | Default | Description |
|---------|------|---------|-------------|
| `min()` | `int` | `0` | 指定允许的最小长度。 |
| `max()` | `int` | `Integer.MAX_VALUE` | 指定允许的最大长度。 |
| `message()` | `String` | `""` | 自定义验证失败时的错误消息。默认为空字符串。 |

## Usage

```java
// 字段级：限制名称长度为 2 ~ 50
@StringLength(min = 2, max = 50)
private String name;

// 参数级
public void setTitle(@StringLength(max = 100) String title) {
    this.title = title;
}

// 自定义错误消息
@StringLength(min = 6, max = 20, message = "密码长度必须在6到20个字符之间")
private String password;
```
