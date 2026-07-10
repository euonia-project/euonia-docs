# ResponseHttpStatusCode

> 标注类对应的 HTTP 响应状态码。
> 用于在异常类上声明其对应的 HTTP 状态码（如 400、404 等），以便框架自动映射。

- **Module**: `core`
- **Type**: `annotation`
- **Package**: `com.euonia.http`
- **Retention**: `RetentionPolicy.RUNTIME`
- **Target**: `TYPE`
- **Author**: damon(zhaorong@outlook.com)

## Annotations

| Annotation | Element | Value | Description |
|-----------|---------|-------|-------------|
| `@Retention` | `value` | `RetentionPolicy.RUNTIME` | 保留策略为运行时 |
| `@Target` | `value` | `TYPE` | 可用于类型声明 |

## Elements

| Element | Type | Default | Description |
|---------|------|---------|-------------|
| `value` | `int` | *(required)* | The HTTP status code associated with the response |
