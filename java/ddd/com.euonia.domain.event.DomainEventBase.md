# DomainEventBase

> 领域事件的基类实现，具体的领域事件可继承此类。提供了处理领域事件的公共属性和方法，例如附加到聚合和转换为事件聚合。

- **Type**: abstract class
- **Package**: `com.euonia.domain.event`
- **Author**: damon(zhaorong@outlook.com)
- **Extends**: `EventBase`
- **Implements**: `DomainEvent`

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `aggregatePayload` | `Object` | 聚合负载对象 |

## Methods

### attach

> 将领域事件附加到指定的聚合。设置发起者 ID、发起者类型和聚合负载。

- **Parameters**:
  - `aggregate` (`Aggregate<ID>`): 领域事件应附加到的聚合

### getEventAggregate

> 检索与此领域事件关联的 {@link EventAggregate}。创建一个包含事件元数据（ID、类型名称、事件意图、事件 ID、时间戳、发起者信息、序号和聚合负载）的新事件聚合实例。

- **Returns**: `EventAggregate` - 与此领域事件关联的 {@link EventAggregate}

### getAggregatePayload

> 获取关联的聚合负载对象。

- **Returns**: `Object` - 聚合负载

### setAggregatePayload

> 设置关联的聚合负载对象。

- **Parameters**:
  - `aggregatePayload` (`Object`): 聚合负载

### getAggregate

> 获取关联的聚合，并强制转换为指定类型。

- **Parameters**:
  - `type` (`Class<A>`): 目标聚合类型
- **Returns**: `A` - 强制转换后的聚合，如果聚合负载为 null 或类型不匹配则返回 null
