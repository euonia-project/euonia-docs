# ChildUnitOfWork
> 将所有操作委托给父级工作单元的工作单元实现。当 UnitOfWorkManager.begin 在当前线程上已有活跃的工作单元且 requiresNew 为 false 时被调用，会返回 ChildUnitOfWork 而非新的顶级单元。所有生命周期方法 —— 保存、提交、回滚、监听器注册 —— 都会转发给父级。completeAsync() 方法在子单元上是空操作，因为只有最外层的工作单元才应触发完成。
- **Type**: class
- **Package**: `com.euonia.uow`
- **Author**: damon(zhaorong@outlook.com)

## Fields
*No public fields.* All fields inherited from `UnitOfWork`.

## Methods

### ChildUnitOfWork
> 创建委托给指定父级工作单元的子工作单元。
- **Parameters**: `parent` (`UnitOfWork`): 父级工作单元

### getItems
- **Returns**: Map\<String, Object\> - 数据项映射

### getContexts
- **Returns**: Map\<String, UnitOfWorkContext\> - 上下文映射

### getOptions
- **Returns**: UnitOfWorkOptions - 活跃的选项

### getOuter
- **Returns**: UnitOfWork - 外部工作单元

### isReserved
- **Returns**: boolean - 是否被预留

### getReservationName
- **Returns**: String - 预留名称

### isDisposed
- **Returns**: boolean - close() 是否已被调用

### isCompleted
- **Returns**: boolean - completeAsync() 是否已成功完成

### getFailure
- **Returns**: Throwable - 失败异常

### addCompletedListener
- **Parameters**: `listener` (`Consumer<UnitOfWorkEvent>`): 回调函数

### addFailedListener
- **Parameters**: `listener` (`Consumer<UnitOfWorkFailure>`): 回调函数

### addDisposedListener
- **Parameters**: `listener` (`Consumer<UnitOfWorkEvent>`): 回调函数

### onCompleted
- **Parameters**: `handler` (`Supplier<CompletionStage<Void>>`): 异步处理器

### initialize
- **Parameters**: `options` (`UnitOfWorkOptions`): 工作单元的选项

### reserve
- **Parameters**: `reservationName` (`String`): 描述性名称

### saveChangesAsync
- **Returns**: CompletionStage\<Void\> - 保存完成后的阶段

### rollbackAsync
- **Returns**: CompletionStage\<Void\> - 回滚完成后的阶段

### completeAsync
> completeAsync() 方法在子单元上是空操作，因为只有最外层的工作单元才应触发完成。
- **Returns**: CompletionStage\<Void\> - 已完成的空阶段

### findContext
- **Parameters**: `key` (`String`): 上下文键
- **Returns**: UnitOfWorkContext - 上下文

### addContext
- **Parameters**: `key` (`String`): 上下文键, `context` (`UnitOfWorkContext`): 要注册的上下文

### getOrAddContext
- **Parameters**: `key` (`String`): 上下文键, `factory` (`Supplier<UnitOfWorkContext>`): 工厂

### setOuter
- **Parameters**: `outer` (`UnitOfWork`): 外部工作单元

### close
> 子单元上空操作。
