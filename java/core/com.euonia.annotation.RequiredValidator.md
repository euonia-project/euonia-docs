# RequiredValidator

> RequiredValidator 是一个用于验证对象是否满足 Required 注解约束的验证器类。它实现了 Validator 接口。

- **Type**: class
- **Package**: `com.euonia.annotation`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### validate

> 执行验证逻辑：如果值为 null，验证失败，返回 "Value is required"。如果值为空字符串且 allowEmpty 为 false，验证失败，返回 "Value must not be empty"。否则验证成功。

- **Parameters**:
  - `annotation` (`Required`): 要验证的注解实例
  - `value` (`Object`): 要验证的值
- **Returns**: `Result` - 验证结果
