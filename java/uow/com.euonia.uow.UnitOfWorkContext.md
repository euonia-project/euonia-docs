# UnitOfWorkContext
> 参与工作单元的事务资源（数据库、消息代理等）的抽象。实现类通过 UnitOfWork.addContext 向 UnitOfWork 注册自己，并接收生命周期回调。
- **Type**: interface
- **Package**: `com.euonia.uow`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### saveChangesAsync
> 将挂起的变更持久化到底层资源，但不提交事务。
- **Returns**: CompletionStage\<Void\> - 在变更保存后完成的阶段

### commitAsync
> 提交事务。
- **Returns**: CompletionStage\<Void\> - 在提交完成后完成的阶段

### rollbackAsync
> 回滚事务。
- **Returns**: CompletionStage\<Void\> - 在回滚完成后完成的阶段

### close
> 释放此上下文持有的所有资源。默认实现不做任何操作。
