# MessageDeliverException

> 消息投递异常，当消息投递过程中发生错误时抛出。

- **Type**: class
- **Package**: `com.euonia.bus.exception`
- **Author**: damon(zhaorong@outlook.com)
- **Extends**: `RuntimeException`

## Constructors

### `MessageDeliverException()`
> 使用默认错误消息构造异常。

### `MessageDeliverException(String message)`
> 使用指定的错误消息构造异常。

**Parameters:**
- `message` (`String`): 详细错误描述

### `MessageDeliverException(String message, Throwable cause)`
> 使用指定的错误消息和原因构造异常。

**Parameters:**
- `message` (`String`): 详细错误描述
- `cause` (`Throwable`): 异常的根因

## Methods

*Inherits all methods from `RuntimeException`.*
