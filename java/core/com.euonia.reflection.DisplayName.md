# DisplayName

> 用于为字段指定显示名称的注解，可在 UI 或错误消息中使用以替代实际的字段名。

- **Module**: `core`
- **Type**: `annotation`
- **Package**: `com.euonia.reflection`
- **Retention**: `RetentionPolicy.RUNTIME`
- **Target**: `FIELD`
- **Author**: damon(zhaorong@outlook.com)

## Annotations

| Annotation | Element | Value | Description |
|-----------|---------|-------|-------------|
| `@Retention` | `value` | `RetentionPolicy.RUNTIME` | 保留策略为运行时 |
| `@Target` | `value` | `FIELD` | 可用于字段 |

## Elements

| Element | Type | Default | Description |
|---------|------|---------|-------------|
| `value` | `String` | *(required)* | 显示名称的值 |
