# RegularExpression

> 用于指定字符串必须匹配的正则表达式的注解。可应用于字段或方法参数，表示该字符串必须符合指定的正则表达式模式。
>
> 该注解支持以下属性：
> - `value`：指定正则表达式模式，必须提供。
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
| `@Validation` | `validator` | [`RegularExpressionValidator.class`](./com.euonia.annotation.RegularExpressionValidator.md) | 关联的验证器实现 |

## Elements

| Element | Type | Default | Description |
|---------|------|---------|-------------|
| `value()` | `String` | *(必填)* | 指定正则表达式模式，必须提供。 |
| `message()` | `String` | `""` | 自定义验证失败时的错误消息，默认为空字符串。 |

## Usage

```java
// 字段级：验证邮箱格式
@RegularExpression("^[\\w.-]+@[\\w.-]+\\.[a-zA-Z]{2,}$")
private String email;

// 参数级：验证手机号格式
public void setPhone(@RegularExpression("^1[3-9]\\d{9}$") String phone) {
    this.phone = phone;
}

// 自定义错误消息
@RegularExpression(value = "^[a-zA-Z0-9]+$", message = "用户名只能包含字母和数字")
private String username;
```
