# RangeValidator

> RangeValidator 是一个用于验证数值是否在指定范围内的验证器类。它实现了 Validator 接口。

- **Type**: class
- **Package**: `com.euonia.annotation`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### validate

> 执行验证逻辑：如果值是一个数字，则检查其是否在注解指定的最小值和最大值之间，并根据 inclusiveMin 和 inclusiveMax 属性判断是否包含边界值。如果值不是数字，则验证成功。

- **Parameters**:
  - `annotation` (`Range`): 要验证的注解实例
  - `value` (`Object`): 要验证的值
- **Returns**: `Result` - 验证结果，包含 boolean 结果和可选的错误消息
