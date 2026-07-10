# HttpStatusException

> HTTP 状态码异常基类，包含 HTTP 状态码和描述错误的消息。
> 可用于表示各种 HTTP 错误，如 400、401、403、404、500 等。

- **Module**: `core`
- **Type**: `class`
- **Package**: `com.euonia.http`
- **Extends**: `RuntimeException`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### HttpStatusException (constructor)

> 使用指定的状态码和消息构造异常。

- **Parameters**:
  - `statusCode` (`int`): HTTP 状态码
  - `message` (`String`): 错误描述

### HttpStatusException (constructor)

> 使用指定的状态码、消息和原因构造异常。

- **Parameters**:
  - `statusCode` (`int`): HTTP 状态码
  - `message` (`String`): 错误描述
  - `cause` (`Throwable`): 异常的根因

### getStatusCode

> 获取 HTTP 状态码。

- **Returns**: `int` - HTTP 状态码
