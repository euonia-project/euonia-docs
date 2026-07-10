# MessageDeliverException
> 消息投递异常，当消息投递过程中发生错误时抛出。
- **Type**: class
- **Package**: `com.euonia.bus.exception`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### this
- **Parameters**:
  - `deliver."` (`"Error occurred during message`): -

### super
- **Parameters**:
  - `message` (``): -

### super
- **Parameters**:
  - `message` (``): -
  - `cause` (``): -

### MessageDeliverException
> 使用默认错误消息构造异常。
- **Returns**: *(constructor)*

### MessageDeliverException
> 使用指定的错误消息构造异常。
- **Parameters**:
  - `message` (`String`): 详细错误描述
- **Returns**: *(constructor)*

### MessageDeliverException
> 使用指定的错误消息和原因构造异常。
- **Parameters**:
  - `message` (`String`): 详细错误描述
  - `cause` (`Throwable`): 异常的根因
- **Returns**: *(constructor)*