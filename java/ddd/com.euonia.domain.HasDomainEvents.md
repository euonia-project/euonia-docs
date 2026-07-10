# HasDomainEvents

> {@link HasDomainEvents} 接口定义了在领域驱动设计（DDD）上下文中可引发和管理领域事件的聚合的契约。聚合是一组领域对象，可以作为数据变更的单一单元处理。聚合根是控制对聚合内其他实体访问的主实体，负责保证整个聚合的一致性。领域事件表示聚合状态中与业务逻辑相关的重大事件或变更，可用于事件溯源、审计或与其他系统集成。

- **Type**: interface
- **Package**: `com.euonia.domain`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### getEvents

> 获取此聚合已引发的领域事件列表。领域事件表示聚合状态中与业务逻辑相关的重大事件或变更，可用于事件溯源、审计或与其他系统集成。

- **Returns**: `List<DomainEvent>` - 此聚合引发的领域事件列表

### registerEvent

> 注册特定类型领域事件的处理器。当引发指定类型的事件时，处理器将被调用。

- **Parameters**:
  - `eventType` (`Class<E>`): 要注册处理器的领域事件类型
  - `handler` (`Consumer<E>`): 当事件引发时要调用的处理器

### raiseEvent

> 引发领域事件。事件将由已注册的处理器处理。

- **Parameters**:
  - `event` (`E`): 要引发的领域事件

### applyEvent

> 将领域事件应用到聚合。此方法通常用于根据事件更新聚合的状态。

- **Parameters**:
  - `event` (`E`): 要应用的领域事件

### clearEvents

> 清除此聚合已引发的所有领域事件。

### attachEvents

> 将所有领域事件附加到聚合。此方法通常用于使用现有事件初始化聚合。
