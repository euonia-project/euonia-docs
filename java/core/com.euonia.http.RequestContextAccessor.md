# RequestContextAccessor

> 请求上下文访问器，基于 ThreadLocal 提供当前请求上下文的存取。私有构造函数，不可实例化。

- **Module**: `core`
- **Type**: `final class`
- **Package**: `com.euonia.http`
- **Author**: damon(zhaorong@outlook.com)

## Static Methods

### get

> 获取当前请求上下文。

- **Returns**: `RequestContext` - 当前请求上下文，如果未设置则返回 null

### set

> 设置当前请求上下文。

- **Parameters**:
  - `context` (`RequestContext`): 当前请求上下文

### remove

> 移除当前请求上下文。
