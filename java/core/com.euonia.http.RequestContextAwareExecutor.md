# RequestContextAwareExecutor

> Provides executors that are aware of the request context, automatically propagating the current context to worker threads.

- **Type**: class
- **Package**: `com.euonia.http`

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
