# ResponseHttpStatusCode

> Annotation that associates an HTTP status code with an exception or response type.

- **Module**: `core`
- **Type**: `annotation`
- **Package**: `com.euonia.http`
- **Retention**: `RetentionPolicy.RUNTIME`
- **Target**: `TYPE`

## Annotations

| Annotation | Element | Value | Description |
|-----------|---------|-------|-------------|
| `@Retention` | `value` | `RetentionPolicy.RUNTIME` | 保留策略为运行时 |
| `@Target` | `value` | `TYPE` | 可用于类型声明 |

## Elements

| Element | Type | Default | Description |
|---------|------|---------|-------------|
| `value` | `int` | *(required)* | The HTTP status code associated with the response |
