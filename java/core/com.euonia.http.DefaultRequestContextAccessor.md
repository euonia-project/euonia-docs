# DefaultRequestContextAccessor

> 默认的请求上下文访问器实现。使用 ThreadLocal 存储请求上下文，确保线程安全。

- **Type**: class
- **Package**: `com.euonia.http`

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `HOLDER` | `ThreadLocal<RequestContext>` | 线程局部存储的请求上下文 |
| `INSTANCE` | `DefaultRequestContextAccessor` | 单例实例 |

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
