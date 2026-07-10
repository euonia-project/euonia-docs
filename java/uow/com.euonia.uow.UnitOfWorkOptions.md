# UnitOfWorkOptions
> 工作单元的配置选项。选项控制事务行为、隔离级别和超时时间。使用 normalize(UnitOfWorkOptions) 与默认选项进行合并。
- **Type**: class
- **Package**: `com.euonia.uow`
- **Author**: damon(zhaorong@outlook.com)

## Fields
*No public fields.*

## Methods

### UnitOfWorkOptions
> 创建默认的、非事务性的选项。

### UnitOfWorkOptions
> 使用给定的事务性标志创建选项。
- **Parameters**: `transactional` (`boolean`): 工作单元是否具有事务性

### UnitOfWorkOptions
> 创建完全指定的选项。
- **Parameters**: `transactional` (`boolean`): 工作单元是否具有事务性, `isolationLevel` (`UnitOfWorkIsolationLevel`): 事务隔离级别，可以为 null, `timeout` (`Duration`): 事务超时时间，可以为 null

### isTransactional
> 返回工作单元是否应为事务性的。
- **Returns**: boolean - 如果是事务性的则返回 true

### setTransactional
- **Parameters**: `transactional` (`boolean`): 事务性标志

### getIsolationLevel
> 返回事务隔离级别，如果未设置则返回 null。
- **Returns**: UnitOfWorkIsolationLevel - 隔离级别，可能为 null

### setIsolationLevel
- **Parameters**: `isolationLevel` (`UnitOfWorkIsolationLevel`): 隔离级别

### getTimeout
> 返回事务超时时间，如果未设置则返回 null。
- **Returns**: Duration - 超时时间，可能为 null

### setTimeout
- **Parameters**: `timeout` (`Duration`): 超时时间

### normalize
> 将给定的选项与此实例合并，使用此实例的值作为任何 null 字段的默认值。
- **Parameters**: `options` (`UnitOfWorkOptions`): 要规范化的选项（不能为 null）
- **Returns**: UnitOfWorkOptions - 规范化后的选项对象（同一实例）
