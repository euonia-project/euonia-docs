# UnitOfWorkManager
> 创建和管理工作单元的入口点。每个管理器持有一组默认的 UnitOfWorkOptions 和一个 UnitOfWorkAccessor，用于跟踪当前线程上的环境工作单元。
- **Type**: class
- **Package**: `com.euonia.uow`
- **Author**: damon(zhaorong@outlook.com)

## Fields
*No public fields.*

## Methods

### UnitOfWorkManager
> 使用默认选项和新的访问器创建管理器。

### UnitOfWorkManager
> 使用给定的访问器和默认选项创建管理器。
- **Parameters**: `accessor` (`UnitOfWorkAccessor`): 用于跟踪当前工作单元的访问器, `defaultOptions` (`UnitOfWorkOptions`): 应用于新工作单元的默认选项

### getCurrent
> 返回与当前线程关联的工作单元，如果没有活跃的工作单元则返回 null。
- **Returns**: UnitOfWork - 当前工作单元，可能为 null

### begin
> 使用给定的选项开启一个新的工作单元。如果当前线程上已有活跃的工作单元且 requiresNew 为 false，则返回一个委托给现有单元的 ChildUnitOfWork。否则创建一个新的顶级单元并将其设置为环境工作单元。
- **Parameters**: `options` (`UnitOfWorkOptions`): 工作单元的选项, `requiresNew` (`boolean`): 如果为 true，始终创建新的顶级单元
- **Returns**: UnitOfWork - 工作单元（必须通过 UnitOfWork.close() 关闭）

### begin
> 使用事务性标志开启工作单元的便捷方法。
- **Parameters**: `transactional` (`boolean`): 工作单元是否具有事务性, `requiresNew` (`boolean`): 如果为 true，始终创建新的顶级单元
- **Returns**: UnitOfWork - 工作单元
