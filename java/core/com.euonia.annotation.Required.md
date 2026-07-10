# Required

> 用于标记字段或方法参数为必填项的注解。被标记的字段或参数在验证时必须非空，除非设置了 `allowEmpty` 为 `true`。
>
> 该注解支持以下属性：
> - `allowEmpty`：是否允许空字符串，默认为 `false`。
> - `message`：自定义验证失败时的错误消息，默认为空字符串。
> - `annotation`：指定注解类型，默认为 `Required.class`。

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
| `@Validation` | `validator` | [`RequiredValidator.class`](./com.euonia.annotation.RequiredValidator.md) | 关联的验证器实现 |

## Elements

| Element | Type | Default | Description |
|---------|------|---------|-------------|
| `allowEmpty()` | `boolean` | `false` | 是否允许空字符串。默认为 `false`，表示不允许空字符串。 |
| `message()` | `String` | `""` | 自定义验证失败时的错误消息。默认为空字符串。 |
| `annotation()` | `Class<? extends Annotation>` | `Required.class` | 指定注解类型，默认为 `Required.class`。 |

## Usage

```java
// 字段级：标记为必填（不允许空字符串）
@Required
private String name;

// 参数级：允许空字符串
public void setNickname(@Required(allowEmpty = true) String nickname) {
    this.nickname = nickname;
}

// 自定义错误消息
@Required(message = "用户名不能为空")
private String username;
```
