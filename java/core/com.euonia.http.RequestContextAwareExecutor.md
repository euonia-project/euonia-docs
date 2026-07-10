# RequestContextAwareExecutor

> 请求上下文感知的执行器工厂，提供能在异步线程中自动传递 `RequestContext` 的 `Executor`。
>
> 提供两种工厂方法：
> - `fromCommonPool()` —— 基于 `ForkJoinPool.commonPool()` 的执行器
> - `fromExecutor()` —— 基于固定大小线程池的执行器

- **Module**: `core`
- **Type**: `class`
- **Package**: `com.euonia.http`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### fromCommonPool

> Creates an executor that wraps the ForkJoinPool.commonPool() with request context propagation.

- **Returns**: `Executor` - A request context-aware executor based on the common ForkJoinPool

### fromExecutor

> Creates a new ThreadPoolExecutor with request context propagation via RequestContextCopyingDecorator.

- **Returns**: `Executor` - A request context-aware thread pool executor (4 threads, queue capacity 1000)

## Inner Types

### TaskWithRequestContext

> Record that wraps a Runnable with its RequestContext for proper context propagation across threads.

- **Type**: record
- **Parameters**:
  - `command` (`Runnable`): The task to execute
  - `context` (`RequestContext`): The request context at the time of submission
