# RequestContextCopyingDecorator

> 请求上下文复制装饰器，将当前线程的请求上下文复制到新线程中执行。
> 在异步任务切换线程时，确保 `RequestContext` 能跨线程传递。

- **Module**: `core`
- **Type**: `class`
- **Package**: `com.euonia.http`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### decorate

> Wraps the given Runnable to capture the current request context and set it during execution, restoring the previous context afterwards.

- **Parameters**:
  - `runnable` (`Runnable`): The task to decorate
- **Returns**: `Runnable` - A decorated runnable with request context propagation
