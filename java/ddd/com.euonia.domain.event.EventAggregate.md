# EventAggregate

> 事件聚合实体，实现了 {@link Aggregate} 接口，用于封装领域事件的元数据和上下文信息。包含事件的 ID、类型名称、事件意图、发起者信息、时间戳、事件负载和序号等属性。这些信息用于事件的持久化、查询和事件溯源。

- **Type**: class
- **Package**: `com.euonia.domain.event`
- **Author**: damon(zhaorong@outlook.com)
- **Implements**: `Aggregate<String>`

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | `String` | 聚合 ID |
| `eventId` | `String` | 事件 ID |
| `timestamp` | `long` | 事件时间戳（Unix 毫秒） |
| `typeName` | `String` | 事件类型名称 |
| `eventIntent` | `String` | 事件意图 |
| `originatorType` | `String` | 发起者类型 |
| `originatorId` | `String` | 发起者 ID |
| `eventPayload` | `Object` | 事件负载对象 |
| `eventSequence` | `long` | 事件序号 |

## Methods

### getId

> 获取聚合的唯一标识符。

- **Returns**: `String` - 聚合的唯一标识符

### setId

> 设置聚合的唯一标识符。

- **Parameters**:
  - `id` (`String`): 聚合的唯一标识符

### getEventId / setEventId

> 获取/设置事件 ID，用于唯一标识事件。

### setTimestamp

> 设置时间戳（支持多种输入格式：{@link Instant}、{@code String}、{@code long}、{@link LocalDateTime}、{@link ZonedDateTime}）。

### getTypeName / setTypeName

> 获取/设置事件类型名称。

### getEventIntent / setEventIntent

> 获取/设置事件意图。

### getOriginatorType / setOriginatorType

> 获取/设置发起者类型。

### getOriginatorId / setOriginatorId

> 获取/设置发起者 ID。

### getEventPayload / setEventPayload

> 获取/设置事件负载对象。

### getEventSequence / setEventSequence

> 获取/设置事件序号。

### getKeys

> 获取聚合的唯一键数组。

- **Returns**: `Object[]` - 包含聚合 ID 的数组

### toString

- **Returns**: `String` - 事件意图字符串
