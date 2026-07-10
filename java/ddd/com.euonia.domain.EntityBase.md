# EntityBase

> 实体的抽象基类实现，提供了 {@link Entity} 接口的基础实现。包含 ID 的 getter/setter、默认的键数组和 {@code toString} 方法。

- **Type**: abstract class
- **Package**: `com.euonia.domain`
- **Author**: damon(zhaorong@outlook.com)
- **Implements**: `Entity<ID>`

## Type Parameters

| Parameter | Bound | Description |
|-----------|-------|-------------|
| `ID` | `Comparable<ID>` | 实体标识符的类型 |

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | `ID` | 实体标识符 |

## Methods

### getId

> 获取实体的唯一标识符。

- **Returns**: `ID` - 实体的唯一标识符

### setId

> 设置实体的唯一标识符。

- **Parameters**:
  - `id` (`ID`): 要为此实体设置的唯一标识符

### getKeys

> 获取唯一标识此实体的键数组。

- **Returns**: `Object[]` - 包含实体标识符的数组

### toString

- **Returns**: `String` - 格式为 `ClassName{id=value}` 的字符串表示
