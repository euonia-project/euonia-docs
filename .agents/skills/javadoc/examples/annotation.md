# 注解的名称

> 描述

- **Type**: `annotation`
- **Package**: `com.euonia.annotation`
- **Retention**：Retention
- **Target**：`Target1`, `Target2`
- **Author**: damon(zhaorong@outlook.com)

## Elements

| Element | Type | Default | Description |
|---------|------|---------|-------------|
| `min()` | `double` | `Double.MIN_VALUE` | 指定允许的最小值。 |
| `max()` | `double` | `Double.MAX_VALUE` | 指定允许的最大值。 |
| `inclusiveMin()` | `boolean` | `false` | 是否包含最小值。为{@code true}时允许指定值等于最小值。 |
| `inclusiveMax()` | `boolean` | `false` | 是否包含最大值。为{@code true}时允许指定值等于最大值。 |
| `message()` | `String` | `""` | 自定义验证失败时的错误消息。默认为空字符串。 |

## Methods

*No methods.*
