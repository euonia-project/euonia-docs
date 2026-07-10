# UnitOfWorkIsolationLevel
> 事务隔离级别，与 JDBC 隔离常量兼容。
- **Type**: enum
- **Package**: `com.euonia.uow`
- **Author**: damon(zhaorong@outlook.com)

## Enum Constants

| Constant | Description |
|----------|-------------|
| `UNSPECIFIED` | 使用底层存储的默认隔离级别 |
| `CHAOS` | 混沌隔离 —— 映射到 TRANSACTION_NONE |
| `READ_UNCOMMITTED` | 可能出现脏读、不可重复读和幻读 |
| `READ_COMMITTED` | 防止脏读；可能出现不可重复读和幻读 |
| `REPEATABLE_READ` | 防止脏读和不可重复读；可能出现幻读 |
| `SNAPSHOT` | 快照隔离 —— 映射到 TRANSACTION_REPEATABLE_READ |
| `SERIALIZABLE` | 防止脏读、不可重复读和幻读 |

## Methods

### toJdbcIsolationLevel
> 将此隔离级别转换为对应的 JDBC 常量。
- **Returns**: int - Connection 事务隔离常量
