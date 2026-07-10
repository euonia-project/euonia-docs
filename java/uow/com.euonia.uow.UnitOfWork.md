# UnitOfWork
> 在单个原子单元内协调事务资源。
- **Type**: class
- **Package**: `com.euonia.uow`
- **Author**: damon(zhaorong@outlook.com)

## Fields
*No public fields.*

## Methods

### UnitOfWork
> 使用默认（非事务性）选项创建工作单元。

### UnitOfWork
> 使用给定的默认选项创建工作单元。
- **Parameters**: `defaultOptions` (`UnitOfWorkOptions`): 回退选项；如果为 null，则使用非事务性默认值

### getId
- **Returns**: String - 此工作单元的唯一标识符

### getItems
> 返回一个可变的映射，用于存储此工作单元范围内的任意数据。
- **Returns**: Map\<String, Object\> - 数据项映射

### getContexts
> 返回已注册的事务上下文的不可修改视图。
- **Returns**: Map\<String, UnitOfWorkContext\> - 上下文映射

### getOptions
- **Returns**: UnitOfWorkOptions - 活跃的选项，初始化前为 null

### getOuter
- **Returns**: UnitOfWork - 外部（父级）工作单元，如果当前已是最外层则返回 null

### isReserved
- **Returns**: boolean - 此工作单元是否已被预留

### getReservationName
- **Returns**: String - 预留名称，如果未被预留则返回 null

### isDisposed
- **Returns**: boolean - close() 是否已被调用

### isCompleted
- **Returns**: boolean - completeAsync() 是否已成功完成

### getFailure
> 返回导致此工作单元失败的异常，如果成功则返回 null。
- **Returns**: Throwable - 失败异常，可能为 null

### addCompletedListener
> 注册一个监听器，当工作单元成功完成时接收通知。
- **Parameters**: `listener` (`Consumer<UnitOfWorkEvent>`): 回调函数

### addFailedListener
> 注册一个监听器，当工作单元失败时接收通知。
- **Parameters**: `listener` (`Consumer<UnitOfWorkFailure>`): 回调函数

### addDisposedListener
> 注册一个监听器，当工作单元被释放时接收通知。
- **Parameters**: `listener` (`Consumer<UnitOfWorkEvent>`): 回调函数

### onCompleted
> 注册一个异步处理器，在完成事件触发之前运行。处理器按顺序链式执行。
- **Parameters**: `handler` (`Supplier<CompletionStage<Void>>`): 异步处理器

### initialize
> 使用给定的选项初始化工作单元（由管理器调用一次）。将提供的选项与此工作单元的默认选项合并。
- **Parameters**: `options` (`UnitOfWorkOptions`): 此工作单元的选项
- **Throws**: `IllegalArgumentException` — 如果 options 为 null, `IllegalStateException` — 如果已经初始化

### reserve
> 为此工作单元预留一个特定目的。
- **Parameters**: `reservationName` (`String`): 描述性名称

### saveChangesAsync
> 保存所有已注册上下文中挂起的变更，但不提交。
- **Returns**: CompletionStage\<Void\> - 当所有上下文保存完成后完成的阶段

### rollbackAsync
> 回滚所有已注册的上下文。
- **Returns**: CompletionStage\<Void\> - 当所有上下文回滚完成后完成的阶段

### completeAsync
> 完成工作单元：保存变更、触发完成处理器、然后通知监听器。只能调用一次。
- **Returns**: CompletionStage\<Void\> - 当工作单元完成后完成的阶段
- **Throws**: `IllegalStateException` — 如果已完成请求已发出

### setOuter
> 设置外部（父级）工作单元以支持嵌套。
- **Parameters**: `outer` (`UnitOfWork`): 外部工作单元

### findContext
> 按键查找已注册的上下文。
- **Parameters**: `key` (`String`): 上下文键
- **Returns**: UnitOfWorkContext - 上下文，如果未找到则返回 null

### addContext
> 在给定键下注册上下文。如果该键下已有上下文，则操作失败。
- **Parameters**: `key` (`String`): 上下文键, `context` (`UnitOfWorkContext`): 要注册的上下文
- **Throws**: `IllegalStateException` — 如果该键下已有上下文

### getOrAddContext
> 获取已有上下文，或使用提供的工厂创建新的上下文。
- **Parameters**: `key` (`String`): 上下文键, `factory` (`Supplier<UnitOfWorkContext>`): 当上下文不存在时用于创建上下文的工厂
- **Returns**: UnitOfWorkContext - 已有或新创建的上下文

### close
> 释放工作单元。关闭所有上下文，如果单元未成功完成则触发失败监听器，并触发释放监听器。幂等 —— 后续调用为空操作。

### notifyCompleted
> 使用给定事件通知所有已注册的完成监听器。
- **Parameters**: `event` (`UnitOfWorkEvent`): 完成事件

### notifyFailed
> 使用给定事件通知所有已注册的失败监听器。
- **Parameters**: `event` (`UnitOfWorkFailure`): 失败事件

### notifyDisposed
> 使用给定事件通知所有已注册的释放监听器。
- **Parameters**: `event` (`UnitOfWorkEvent`): 释放事件
