# EventBase

> {@link Event} 接口的基础实现。为所有事件提供公共属性和方法，包括事件意图、发起者类型、发起者 ID 和事件序号。子类可以扩展此类以创建具有额外属性和行为的特定事件类型。事件属性存储在内部的 {@code properties} 映射中，支持通过 {@link #get(String, Class)} 方法进行类型安全的属性值转换。

- **Type**: abstract class
- **Package**: `com.euonia.domain.event`
- **Author**: damon(zhaorong@outlook.com)
- **Implements**: `Event`

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `PROPERTY_EVENT_INTENT` | `String` | 事件意图属性的存储键 |
| `PROPERTY_ORIGINATOR_TYPE` | `String` | 发起者类型属性的存储键 |
| `PROPERTY_ORIGINATOR_ID` | `String` | 发起者 ID 属性的存储键 |
| `properties` | `Map<String, String>` | 事件属性存储 |
| `sequence` | `long` | 事件序号，基于当前时间的毫秒值 |

## Methods

### EventBase

> 构造事件基类实例，自动将事件意图设置为当前类的全限定名。

### get

> 根据键获取属性值，如果键不存在则返回 null。

- **Parameters**:
  - `property` (`String`): 属性键
- **Returns**: `String` - 属性值，如果键不存在则返回 null

### set

> 设置属性键值对。

- **Parameters**:
  - `property` (`String`): 属性键
  - `value` (`String`): 属性值

### get

> 根据键获取属性值，并通过 {@link TypeHelper#coerceValue} 强制转换为指定类型。

- **Parameters**:
  - `property` (`String`): 属性键
  - `castType` (`Class<T>`): 目标类型
- **Returns**: `T` - 强制转换后的属性值，如果键不存在则返回 null

### getEventIntent / setEventIntent

> 获取/设置事件意图，表示事件的目的或含义。

### getSequence / setSequence

> 获取/设置事件的序号。

### getOriginatorType / setOriginatorType

> 获取/设置事件的发起者类型。

### getOriginatorId / setOriginatorId

> 获取/设置事件的发起者 ID。
