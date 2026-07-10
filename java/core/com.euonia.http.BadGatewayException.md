# BadGatewayException

> HTTP 502 Bad Gateway 异常，表示服务器作为网关或代理时从上游服务器收到无效响应。

- **Module**: `core`
- **Type**: `class`
- **Package**: `com.euonia.http`
- **Extends**: [`HttpStatusException`](./com.euonia.http.HttpStatusException.md)
- **Author**: damon(zhaorong@outlook.com)

## Methods

### BadGatewayException (constructor)

> 使用指定的消息构造异常。

- **Parameters**:
  - `message` (`String`): 错误描述

### BadGatewayException (constructor)

> 使用指定的消息和原因构造异常。

- **Parameters**:
  - `message` (`String`): 错误描述
  - `cause` (`Throwable`): 异常的根因
