# RequestContextCopyingDecorator

> Decorates a Runnable with request context copying logic, ensuring that the original request context is available during task execution and properly restored afterwards.

- **Type**: class
- **Package**: `com.euonia.http`

## Methods

### decorate

> Wraps the given Runnable to capture the current request context and set it during execution, restoring the previous context afterwards.

- **Parameters**:
  - `runnable` (`Runnable`): The task to decorate
- **Returns**: `Runnable` - A decorated runnable with request context propagation
