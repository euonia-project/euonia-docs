# UnitOfWorkFailure
> 工作单元失败时引发的事件 —— 可能由于异常或显式回滚导致。通过 UnitOfWork.addFailedListener 注册的监听器会收到此类的实例。
- **Type**: class
- **Package**: `com.euonia.uow`
- **Author**: damon(zhaorong@outlook.com)

## Fields
*No public fields.*

## Methods

### UnitOfWorkFailure
> 创建一个新的失败事件。
- **Parameters**: `unitOfWork` (`UnitOfWork`): 失败的工作单元, `exception` (`Throwable`): 导致失败的异常，可能为 null, `rollback` (`boolean`): 是否触发了回滚

### getException
> 返回导致失败的异常。如果失败是由显式回滚触发的，则返回 null。
- **Returns**: Throwable - 异常，可能为 null

### isRollback
> 返回是否执行了回滚。
- **Returns**: boolean - 如果工作单元已回滚则返回 true
