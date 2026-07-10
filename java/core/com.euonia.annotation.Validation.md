# Validation

> 用于指定验证器的元注解。该注解可应用于其他注解类型上，用于关联一个验证器类。
>
> 该注解支持以下属性：
> - `validator`：指定验证器类，该类必须实现 [`Validator`](./com.euonia.annotation.Validator.md) 接口。

- **Module**: `core`
- **Type**: `annotation`
- **Package**: `com.euonia.annotation`
- **Retention**: `RetentionPolicy.RUNTIME`
- **Target**: `ANNOTATION_TYPE`
- **Author**: damon(zhaorong@outlook.com)

## Inheritance

- 隐式继承 `java.lang.annotation.Annotation`

## Annotations

| Annotation | Element | Value | Description |
|-----------|---------|-------|-------------|
| `@Retention` | `value` | `RetentionPolicy.RUNTIME` | 保留策略为运行时 |
| `@Target` | `value` | `ANNOTATION_TYPE` | 只能用于其他注解类型上 |

## Elements

| Element | Type | Default | Description |
|---------|------|---------|-------------|
| `validator()` | `Class<? extends Validator<?>>` | *(必填)* | 指定验证器类，该类必须实现 [`Validator`](./com.euonia.annotation.Validator.md) 接口。 |

## Usage

```java
// 在自定义校验注解上使用 @Validation 关联验证器
@Retention(RetentionPolicy.RUNTIME)
@Target({ElementType.FIELD, ElementType.PARAMETER})
@Validation(validator = MyCustomValidator.class)
public @interface MyCustomConstraint {
    String message() default "";
}
```
