# Range
> 用于指定数值范围的注解。可应用于字段或方法参数，表示该数值必须在指定的最小值和最大值之间。 <p> 该注解支持以下属性： <ul> <li>{@code min}：指定允许的最小值，默认为 {@code Double.MIN_VALUE}。</li> <li>{@code max}：指定允许的最大值，默认为 {@code Double.MAX_VALUE}。</li> <li>{@code inclusiveMin}：是否包含最小值，默认为 {@code false}。</li> <li>{@code inclusiveMax}：是否包含最大值，默认为 {@code false}。</li> </ul>
- **Type**: annotation
- **Package**: `com.euonia.annotation`
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
