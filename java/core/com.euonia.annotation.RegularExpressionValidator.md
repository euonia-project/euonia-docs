# RegularExpressionValidator

> RegularExpressionValidator 是一个用于验证对象是否满足 RegularExpression 注解约束的验证器类。它实现了 Validator 接口。

- **Type**: class
- **Package**: `com.euonia.annotation`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### validate

> 执行验证逻辑：如果值是一个字符串，则检查该字符串是否匹配指定的正则表达式模式。如果不匹配，返回失败结果。如果值不是字符串，则验证成功。

- **Parameters**:
  - `annotation` (`RegularExpression`): 要验证的注解实例
  - `value` (`Object`): 要验证的值
- **Returns**: `Result` - 验证结果
