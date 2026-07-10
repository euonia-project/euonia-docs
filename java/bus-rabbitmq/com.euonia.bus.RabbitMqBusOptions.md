# RabbitMqBusOptions

> RabbitMQ 总线传输的配置选项。该类封装了与 RabbitMQ 建立连接所需的所有必要设置，以及消息处理的各种参数，如交换器和队列配置、重试策略等。

- **Type:** `final class`
- **Package:** `com.euonia.bus`
- **Author:** damon(zhaorong@outlook.com)

## Fields

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `enabledSupplier` | `Supplier<Boolean>` | `() -> true` | 是否启用该传输 |
| `name` | `String` | `RabbitMqTransport.class.getSimpleName()` | 传输名称 |
| `host` | `String` | `"localhost"` | 主机地址 |
| `username` | `String` | `"guest"` | 用户名 |
| `password` | `String` | `"guest"` | 密码 |
| `virtualHost` | `String` | `"/"` | 虚拟主机 |
| `connection` | `String` | (null) | AMQP 连接字符串（显式设置时优先于 host/port 等） |
| `port` | `int` | `5672` | 端口号 |
| `exchangeNamePrefix` | `String` | `RabbitMqConstants.DEFAULT_EXCHANGE_NAME_PREFIX` | 交换器名称前缀 |
| `queueNamePrefix` | `String` | `RabbitMqConstants.DEFAULT_QUEUE_NAME_PREFIX` | 队列名称前缀 |
| `rpcQueuePrefix` | `String` | `RabbitMqConstants.DEFAULT_RPC_QUEUE_NAME_PREFIX` | RPC 队列名称前缀 |
| `mandatory` | `boolean` | `true` | 是否为强制模式 |
| `prefetchCount` | `int` | `1` | 预取计数 |
| `retryDelay` | `long` | `5000L` | 重试延迟（毫秒） |
| `retryAttempts` | `int` | `3` | 重试次数 |
| `subscriptionId` | `String` | (null) | 订阅标识符 |
| `deadLetterEnabled` | `boolean` | `true` | 是否启用死信队列。启用后，被拒绝的消息将被路由到死信交换器。基于 RabbitMQ 的 Dead Letter Exchange (DLX) 机制。 |
| `deadLetterExchangePrefix` | `String` | `RabbitMqConstants.DEFAULT_DLX_EXCHANGE_PREFIX` | 死信交换器名称前缀 |
| `deadLetterQueuePrefix` | `String` | `RabbitMqConstants.DEFAULT_DLQ_QUEUE_NAME_PREFIX` | 死信队列名称前缀 |

## Methods

| Name | Return | Description |
|------|--------|-------------|
| `isEnabled()` | `boolean` | 检查是否启用该传输 |
| `setEnabled(Supplier<Boolean>)` | `void` | 设置启用状态的供应器 |
| `getName()` | `String` | 获取传输名称 |
| `setName(String)` | `void` | 设置传输名称 |
| `getHost()` | `String` | 获取主机地址 |
| `setHost(String)` | `void` | 设置主机地址 |
| `getPort()` | `int` | 获取端口号 |
| `setPort(int)` | `void` | 设置端口号 |
| `getUsername()` | `String` | 获取用户名 |
| `setUsername(String)` | `void` | 设置用户名 |
| `getPassword()` | `String` | 获取密码 |
| `setPassword(String)` | `void` | 设置密码 |
| `getVirtualHost()` | `String` | 获取虚拟主机 |
| `setVirtualHost(String)` | `void` | 设置虚拟主机 |
| `getConnection()` | `String` | 构建并返回 RabbitMQ 连接字符串。如果显式设置了 `connection` 属性，则直接返回；否则基于 host、port、username、password 和 virtualHost 属性自动构建 AMQP 连接字符串 |
| `setConnection(String)` | `void` | 设置 RabbitMQ 连接字符串 |
| `getExchangeNamePrefix()` | `String` | 获取交换器名称前缀 |
| `setExchangeNamePrefix(String)` | `void` | 设置交换器名称前缀 |
| `getQueueNamePrefix()` | `String` | 获取队列名称前缀 |
| `setQueueNamePrefix(String)` | `void` | 设置队列名称前缀 |
| `getRpcQueuePrefix()` | `String` | 获取 RPC 队列前缀 |
| `setRpcQueuePrefix(String)` | `void` | 设置 RPC 队列前缀 |
| `isMandatory()` | `boolean` | 是否为强制模式 |
| `setMandatory(boolean)` | `void` | 设置是否为强制模式 |
| `getPrefetchCount()` | `int` | 获取预取计数 |
| `setPrefetchCount(int)` | `void` | 设置预取计数 |
| `getRetryDelay()` | `long` | 获取重试延迟时间 |
| `setRetryDelay(long)` | `void` | 设置重试延迟时间 |
| `getRetryAttempts()` | `int` | 获取重试次数 |
| `setRetryAttempts(int)` | `void` | 设置重试次数 |
| `getSubscriptionId()` | `String` | 获取订阅 ID |
| `setSubscriptionId(String)` | `void` | 设置订阅 ID |
| `generateQueueName(String, String)` | `String` | 生成队列名称，格式为：`{prefix}:{channelName}@{subscriptionId}` |
| `isDeadLetterEnabled()` | `boolean` | 是否启用死信队列 |
| `setDeadLetterEnabled(boolean)` | `void` | 设置是否启用死信队列 |
| `getDeadLetterExchangePrefix()` | `String` | 获取死信交换器名称前缀 |
| `setDeadLetterExchangePrefix(String)` | `void` | 设置死信交换器名称前缀 |
| `getDeadLetterQueuePrefix()` | `String` | 获取死信队列名称前缀 |
| `setDeadLetterQueuePrefix(String)` | `void` | 设置死信队列名称前缀 |
| `generateDlxExchangeName(String)` | `String` | 生成死信交换器名称 |
| `generateDlqQueueName(String)` | `String` | 生成死信队列名称（入参 channelName 与原始队列一致以确保唯一性） |
