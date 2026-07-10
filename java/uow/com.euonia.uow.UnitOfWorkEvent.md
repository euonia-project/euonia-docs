# UnitOfWorkEvent
> 工作单元完成或被释放时引发的事件。通过 UnitOfWork.addCompletedListener 和 UnitOfWork.addDisposedListener 注册的监听器会收到此类的实例。
- **Type**: class
- **Package**: `com.euonia.uow`
- **Author**: damon(zhaorong@outlook.com)

## Fields
*No public fields.*

## Methods

### UnitOfWorkEvent
> 为给定的工作单元创建新的事件。
- **Parameters**: `unitOfWork` (`UnitOfWork`): 触发事件的工作单元

### getUnitOfWork
> 返回触发此事件的工作单元。
- **Returns**: UnitOfWork - 关联的工作单元
