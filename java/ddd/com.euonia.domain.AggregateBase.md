# AggregateBase

> {@link AggregateBase} 是领域驱动设计（DDD）上下文中实现 {@link Aggregate} 接口的抽象基类。提供了在聚合根内管理领域事件及其处理器的公共实现。聚合是一组领域对象，可以作为数据变更的单一单元处理。聚合根是控制对聚合内其他实体访问的主实体，负责保证整个聚合的一致性。

- **Type**: abstract class
- **Package**: `com.euonia.domain`
- **Author**: damon(zhaorong@outlook.com)
- **Extends**: `EntityBase<ID>`
- **Implements**: `Aggregate<ID>`, `HasDomainEvents`

## Type Parameters

| Parameter | Bound | Description |
|-----------|-------|-------------|
| `ID` | `Comparable<ID>` | 聚合标识符的类型，必须可比较 |

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `events` | `List<DomainEvent>` | 已引发的领域事件列表 |
| `eventHandlers` | `ConcurrentMap<Class<? extends DomainEvent>, List<Consumer<DomainEvent>>>` | 事件类型到处理器列表的映射 |

## Methods

### registerEvent

> 注册特定类型领域事件的处理器。当引发指定类型的事件时，处理器将被调用。

- **Parameters**:
  - `eventType` (`Class<E>`): 要注册处理器的事件类型
  - `handler` (`Consumer<E>`): 当事件引发时要调用的处理器

### getEvents

> 获取此聚合已引发的领域事件列表。

- **Returns**: `List<DomainEvent>` - 此聚合引发的领域事件列表

### raiseEvent

> 引发领域事件。事件将由已注册的处理器处理。

- **Parameters**:
  - `event` (`E`): 要引发的领域事件

### applyEvent

> 应用领域事件，调用注册的处理器来处理该事件。

- **Parameters**:
  - `event` (`E`): 要应用的领域事件

### clearEvents

> 清除已引发的领域事件列表。此方法通常在事件处理完成后调用，以便重置聚合的事件状态。

### attachEvents

> 将所有已引发的领域事件附加到当前聚合实例。此方法会遍历已引发的事件列表，并调用每个事件的 attach 方法，将其与当前聚合关联起来。
