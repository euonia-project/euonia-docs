# StringLengthValidator

> StringLengthValidator 是一个用于验证字符串长度是否在指定范围内的验证器类。它实现了 Validator 接口。

- **Type**: class
- **Package**: `com.euonia.annotation`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### validate

> 执行验证逻辑：如果值是一个字符串，则检查其长度是否在注解指定的最小值和最大值之间。如果长度不在指定范围内，返回失败结果。如果值不是字符串，则验证成功。

- **Parameters**:
  - `annotation` (`StringLength`): 要验证的注解实例
  - `value` (`Object`): 要验证的值
- **Returns**: `Result` - 验证结果
