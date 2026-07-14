# MessageTransportException

> 消息传输异常，表示总线系统中消息传输过程中发生的异常。
>
> 该异常在消息发送或接收出现问题时抛出，如网络错误、序列化问题或其他与传输相关的问题。

- **Type**: class
- **Package**: `com.euonia.bus.exception`
- **Author**: damon(zhaorong@outlook.com)
- **Extends**: `RuntimeException`

## Constructors

### `MessageTransportException(String message)`
> 使用指定的详细错误消息构造异常。

**Parameters:**
- `message` (`String`): 详细错误描述

### `MessageTransportException(String message, Throwable cause)`
> 使用指定的详细错误消息和原因构造异常。

**Parameters:**
- `message` (`String`): 详细错误描述
- `cause` (`Throwable`): 异常的根因

## Methods

*Inherits all methods from `RuntimeException`.*
