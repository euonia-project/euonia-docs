# RegularExpression
> 用于指定字符串必须匹配的正则表达式的注解。可应用于字段或方法参数，表示该字符串必须符合指定的正则表达式模式。 <p> 该注解支持以下属性： <ul> <li>{@code value}：指定正则表达式模式，必须提供。</li> <li>{@code message}：自定义验证失败时的错误消息，默认为空字符串。</li> </ul> <p>
- **Type**: annotation
- **Package**: `com.euonia.annotation`
- **Author**: damon(zhaorong@outlook.com)

## Elements

| Element | Type | Default | Description |
|---------|------|---------|-------------|
| `value()` | `String` | `` | 指定正则表达式模式，必须提供。 |
| `message()` | `String` | `""` | 自定义验证失败时的错误消息，默认为空字符串。 |

## Methods

*No methods.*
