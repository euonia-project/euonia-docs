# UnitOfWorkAccessor
> 当前线程环境 UnitOfWork 的线程本地持有者。每个线程都有自己独立的工作单元，因此在 servlet 容器等线程-请求环境下使用是安全的。
- **Type**: class
- **Package**: `com.euonia.uow`
- **Author**: damon(zhaorong@outlook.com)

## Fields
*No public fields.*

## Methods

### getCurrentUnitOfWork
> 返回与当前线程关联的工作单元。如果没有活跃的工作单元则返回 null。
- **Returns**: UnitOfWork - 当前工作单元，可能为 null

### setCurrentUnitOfWork
> 为当前线程设置工作单元。传入 null 将移除关联。
- **Parameters**: `unitOfWork` (`UnitOfWork`): 要关联的工作单元，传入 null 以清除
