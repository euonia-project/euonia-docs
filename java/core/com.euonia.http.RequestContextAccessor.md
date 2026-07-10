# RequestContextAccessor

> 定义请求上下文访问器的接口。

- **Type**: interface
- **Package**: `com.euonia.http`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### getContext

> 获取当前请求上下文。

- **Returns**: `RequestContext` - 当前请求上下文

### setContext

> 设置当前请求上下文。

- **Parameters**:
  - `context` (`RequestContext`): 当前请求上下文

### removeContext

> 移除当前请求上下文。

### get

> 静态便捷方法：获取当前请求上下文。

- **Returns**: `RequestContext` - 当前请求上下文

### set

> 静态便捷方法：设置当前请求上下文。

- **Parameters**:
  - `context` (`RequestContext`): 当前请求上下文

### remove

> 静态便捷方法：移除当前请求上下文。
