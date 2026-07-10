# DefaultRequestContextAccessor

> `RequestContextAccessor` 的默认实现，基于 `ThreadLocal` 存储请求上下文。
> 采用单例模式，每个线程拥有独立的上下文副本。

- **Module**: `core`
- **Type**: `final class`
- **Package**: `com.euonia.http`
- **Implements**: [`RequestContextAccessor`](./com.euonia.http.RequestContextAccessor.md)
- **Author**: damon(zhaorong@outlook.com)

## Methods

### getInstance

> 获取 DefaultRequestContextAccessor 的单例实例。

- **Returns**: `DefaultRequestContextAccessor` - 单例实例

### setContext

> 设置当前请求上下文（到 ThreadLocal）。

- **Parameters**:
  - `context` (`RequestContext`): 当前请求上下文

### removeContext

> 移除当前请求上下文（从 ThreadLocal）。

### getContext

> 获取当前请求上下文（从 ThreadLocal）。

- **Returns**: `RequestContext` - 当前请求上下文

### get

> 静态便捷方法：获取当前请求上下文。

- **Returns**: `RequestContext` - 当前请求上下文

### set

> 静态便捷方法：设置当前请求上下文。

- **Parameters**:
  - `context` (`RequestContext`): 当前请求上下文

### remove

> 静态便捷方法：移除当前请求上下文。
