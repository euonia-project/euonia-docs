# OutboxPublisher
> 投递箱发布器，异地轮询 `OutboxStore` 并将消息发送到 `Bus`。
- **Type**: class
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `LOGGER` | `Logger` | 日志记录器 |
| `bus` | `Bus` | 消息总线 |
| `outboxStore` | `OutboxStore` | 投递箱存储 |
| `scheduler` | `ScheduledExecutorService` | 调度线程池 |
| `interval` | `long` | 轮询间隔 |
| `intervalUnit` | `TimeUnit` | 间隔时间单位 |

## Methods
### OutboxPublisher
> 创建 OutboxPublisher 实例。
- **Parameters**:
  - `bus` (`Bus`): 消息总线
  - `outboxStore` (`OutboxStore`): 投递箱存储
  - `interval` (`long`): 轮询间隔
  - `intervalUnit` (`TimeUnit`): 间隔时间单位

### start
> 启动投递箱发布器，开始定期轮询。

### flush
> 立即执行一次刷新，发布所有待处理消息。

### shutdown
> 关闭投递箱发布器，在停止前执行最后一次刷新。

### close
> `AutoCloseable` 接口实现，委托给 `shutdown()`。
