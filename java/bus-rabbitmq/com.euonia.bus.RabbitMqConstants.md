# RabbitMqConstants

> RabbitMQ 总线模块的内部常量定义。定义 RabbitMQ 交换器、队列和 RPC 队列的默认名称前缀。这些前缀用于在 RabbitMQ 中生成唯一的交换器和队列名称。

- **Type:** `class` (package-private)
- **Package:** `com.euonia.bus`
- **Author:** damon(zhaorong@outlook.com)

## Fields

| Name | Type | Value | Description |
|------|------|-------|-------------|
| `DEFAULT_EXCHANGE_NAME_PREFIX` | `static final String` | `"$nerosoft.euonia.exchange"` | 默认交换器名称前缀 |
| `DEFAULT_QUEUE_NAME_PREFIX` | `static final String` | `"$nerosoft.euonia.queue"` | 默认队列名称前缀 |
| `DEFAULT_RPC_QUEUE_NAME_PREFIX` | `static final String` | `"$nerosoft.euonia.request"` | 默认 RPC 队列名称前缀 |
| `DEFAULT_DLX_EXCHANGE_PREFIX` | `static final String` | `"$nerosoft.euonia.dlx"` | 死信队列交换器名称前缀 |
| `DEFAULT_DLQ_QUEUE_NAME_PREFIX` | `static final String` | `"$nerosoft.euonia.dlq"` | 死信队列名称前缀 |
| `DEFAULT_DLX_ROUTING_KEY` | `static final String` | `"dead-letter"` | 死信路由键 |

## Methods

*No methods — this is a constants-only class.*
