# AuditRecord

> 审计记录实体，用于记录对领域实体的操作审计信息。包含被审计实体的名称、ID、操作类型、时间戳以及执行操作的用户信息。继承自 {@link EntityBase}，支持自定义 ID 类型。

- **Type**: class
- **Package**: `com.euonia.domain.auditing`
- **Author**: damon(zhaorong@outlook.com)
- **Extends**: `EntityBase<ID>`

## Type Parameters

| Parameter | Bound | Description |
|-----------|-------|-------------|
| `ID` | `Comparable<ID>` | 实体 ID 的类型 |

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `entityName` | `String` | 被审计的实体名称 |
| `entityId` | `String` | 被审计实体的 ID |
| `action` | `String` | 执行的操作类型（如 CREATE、UPDATE、DELETE） |
| `timestamp` | `Instant` | 操作发生的时间戳 |
| `comment` | `String` | 审计备注 |
| `userId` | `String` | 执行操作的用户 ID |
| `userName` | `String` | 执行操作的用户名 |

## Methods

### AuditRecord

> 使用指定的实体名称、实体 ID、操作类型和时间戳构造审计记录。

- **Parameters**:
  - `entityName` (`String`): 实体名称
  - `entityId` (`String`): 实体 ID
  - `action` (`String`): 操作类型
  - `timestamp` (`Instant`): 操作时间戳

### AuditRecord

> 使用指定的实体名称、实体 ID 和操作类型构造审计记录，时间戳自动设为当前时间。

- **Parameters**:
  - `entityName` (`String`): 实体名称
  - `entityId` (`String`): 实体 ID
  - `action` (`String`): 操作类型

### AuditRecord

> 使用实体类、实体 ID 和操作类型构造审计记录，实体名称从类的简单名称获取。

- **Parameters**:
  - `entityClass` (`Class<?>`): 实体类
  - `entityId` (`String`): 实体 ID
  - `action` (`String`): 操作类型

### getEntityName

> 获取被审计的实体名称。

- **Returns**: `String` - 实体名称

### getEntityId

> 获取被审计实体的 ID。

- **Returns**: `String` - 实体 ID

### getAction

> 获取操作类型。

- **Returns**: `String` - 操作类型

### getTimestamp

> 获取操作时间戳。

- **Returns**: `Instant` - 操作时间戳

### getComment

> 获取审计备注。

- **Returns**: `String` - 审计备注

### setComment

> 设置审计备注。

- **Parameters**:
  - `comment` (`String`): 审计备注

### getUserId

> 获取执行操作的用户 ID。

- **Returns**: `String` - 用户 ID

### setUserId

> 设置执行操作的用户 ID。

- **Parameters**:
  - `userId` (`String`): 用户 ID

### getUserName

> 获取执行操作的用户名。

- **Returns**: `String` - 用户名

### setUserName

> 设置执行操作的用户名。

- **Parameters**:
  - `userName` (`String`): 用户名
