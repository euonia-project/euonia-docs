# StringLength

> 用于指定字符串长度范围的注解。可应用于字段或方法参数，表示该字符串的长度必须在指定的最小值和最大值之间。

- **Type**: annotation
- **Package**: `com.euonia.annotation`
- **Author**: damon(zhaorong@outlook.com)

## Elements

| Element | Type | Default | Description |
|---------|------|---------|-------------|
| `min` | `int` | `0` | 指定允许的最小长度 |
| `max` | `int` | `Integer.MAX_VALUE` | 指定允许的最大长度 |
| `message` | `String` | `""` | 自定义验证失败时的错误消息 |
