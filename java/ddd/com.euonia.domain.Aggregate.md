# Aggregate

> {@link Aggregate} 接口表示领域驱动设计（DDD）上下文中的聚合根。聚合是一组领域对象，可以作为数据变更的单一单元处理。聚合根是控制对聚合内其他实体访问的主实体，负责保证整个聚合的一致性。

- **Type**: interface
- **Package**: `com.euonia.domain`
- **Author**: damon(zhaorong@outlook.com)
- **Extends**: `Entity<ID>`

## Type Parameters

| Parameter | Bound | Description |
|-----------|-------|-------------|
| `ID` | `Comparable<ID>` | 聚合标识符的类型 |

## Methods

_Inherited from `Entity<ID>`._
