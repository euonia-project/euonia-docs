# SnowflakeId

> SnowflakeId 是一个分布式唯一 ID 生成器，灵感来源于 Twitter 的 Snowflake 算法。它基于当前时间戳、工作节点 ID、数据中心 ID 和序列号生成 64 位唯一 ID。生成的 ID 可按时间排序，且可在分布式环境中生成，无需节点间协调。自定义纪元设置为 2021 年 1 月 1 日。

- **Type**: class
- **Package**: `com.euonia.core`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `EPOCH` | `long` | 自定义纪元：2021-01-01 00:00:00 UTC（1609459200000L） |
| `WORKER_ID_BITS` | `long` | 工作节点 ID 位数：5 |
| `DATACENTER_ID_BITS` | `long` | 数据中心 ID 位数：5 |
| `SEQUENCE_BITS` | `long` | 序列号位数：12 |
| `workerId` | `long` | 工作节点 ID |
| `datacenterId` | `long` | 数据中心 ID |
| `sequence` | `long` | 序列号 |
| `lastTimestamp` | `long` | 上一次生成 ID 的时间戳 |

## Methods

### getInstance

> 获取 SnowflakeId 的默认实例，使用 workerId 和 datacenterId 都为 0。

- **Returns**: `SnowflakeId` - 默认的 SnowflakeId 实例

### getInstance

> 使用指定的 workerId 和 datacenterId 获取实例。

- **Parameters**:
  - `workerId` (`long`): 工作节点 ID
  - `datacenterId` (`long`): 数据中心 ID
- **Returns**: `SnowflakeId` - 新实例

### nextId

> 生成下一个唯一 ID。该方法是线程安全的，确保在多线程环境下生成的 ID 仍然唯一。如果系统时钟回退，将抛出异常。

- **Returns**: `long` - 下一个唯一的 64 位 ID
