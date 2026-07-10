# Validation

> 用于指定验证器的元注解。该注解可应用于其他注解类型上，用于关联一个验证器类，该类必须实现 `Validator` 接口。

- **Type**: annotation
- **Package**: `com.euonia.annotation`
- **Author**: damon(zhaorong@outlook.com)

## Elements

| Element | Type | Default | Description |
|---------|------|---------|-------------|
| `validator` | `Class<? extends Validator<?>>` | *(required)* | 指定验证器类，该类必须实现 `Validator` 接口 |
