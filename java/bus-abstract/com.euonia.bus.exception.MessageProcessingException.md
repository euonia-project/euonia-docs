# MessageProcessingException
> 消息处理异常，表示总线系统中消息处理过程中发生的异常。
> <p>
> 该异常在消息处理或操作出现问题时抛出，如验证错误、业务逻辑错误或其他与处理相关的问题。
- **Type**: class
- **Package**: `com.euonia.bus.exception`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### super

### super
- **Parameters**:
  - `message` (``): -
  - `cause` (``): -

### MessageProcessingException
> 构造没有详细错误消息的异常。
- **Returns**: *(constructor)*

### MessageProcessingException
> 使用指定的详细错误消息构造异常。
- **Parameters**:
  - `message` (`String`): 详细错误描述
- **Returns**: *(constructor)*

### MessageProcessingException
> 使用指定的详细错误消息和原因构造异常。
- **Parameters**:
  - `message` (`String`): 详细错误描述
  - `cause` (`Throwable`): 异常的根因
- **Returns**: *(constructor)*