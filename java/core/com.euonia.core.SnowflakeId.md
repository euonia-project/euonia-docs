# SnowflakeId

> SnowflakeId 是一个分布式唯一 ID 生成器，灵感来源于 Twitter 的 Snowflake 算法。
> 它基于当前时间戳、工作节点 ID、数据中心 ID 和序列号生成 64 位唯一 ID。
> 生成的 ID 可按时间排序，且可在分布式环境中生成，无需节点间协调。
>
> 生成的 ID 结构如下：
> - 41 位用于时间戳（自自定义纪元以来的毫秒数）
> - 5 位用于数据中心 ID
> - 5 位用于工作节点 ID
> - 12 位用于序列号
>
> 此实现允许每个工作节点每毫秒生成最多 1024 个唯一 ID，并支持最多 32 个数据中心，每个数据中心最多 32 个工作节点。
> 自定义纪元设置为 2021 年 1 月 1 日。

- **Module**: `core`
- **Type**: `final class`
- **Package**: `com.euonia.core`
- **Author**: damon(zhaorong@outlook.com)

## Constants

| Constant | Value | Description |
|----------|-------|-------------|
| `MAX_WORKER_ID` | `31` | 最大工作节点 ID |
| `MAX_DATACENTER_ID` | `31` | 最大数据中心 ID |
| `MAX_SEQUENCE` | `4095` | 最大序列号 |

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

## Usage

```java
SnowflakeId idGen = SnowflakeId.getInstance();
long id = idGen.nextId();
```
