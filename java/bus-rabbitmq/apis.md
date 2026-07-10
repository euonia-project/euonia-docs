# Euonia Bus-RabbitMQ 模块 API 文档

## 概述

Euonia 消息总线的 RabbitMQ 传输适配器。基于 `bus-abstract` 的抽象契约，提供通过 RabbitMQ AMQP 代理的消息传递实现，支持单播队列、多播 topic 交换和请求-响应 RPC 模式。

- **Maven 坐标**: `com.euonia:bus-rabbitmq`
- **Java 模块名**: `com.euonia.bus`
- **依赖**: `com.euonia:core`, `com.euonia:pipeline`, `com.euonia:bus-abstract`, `com.euonia:bus-core`

## 导出包

### com.euonia.bus

| 类 | 类型 | 说明 |
|----|------|------|
| [RabbitMqTransport](./com.euonia.bus.RabbitMqTransport.md) | class | Transport 接口的 RabbitMQ 实现，含 Failsafe 重试 |
| [RabbitMqBusOptions](./com.euonia.bus.RabbitMqBusOptions.md) | class | RabbitMQ 配置选项（host、port、exchange/queue 前缀、重试、DLX） |
| [RabbitMqConstants](./com.euonia.bus.RabbitMqConstants.md) | class | RabbitMQ 内部常量（交换器/队列/DLX 名称前缀） |
| [RabbitMqRecipient](./com.euonia.bus.RabbitMqRecipient.md) | abstract class | 接收者抽象基类：事件监听、回复属性、DLX 基础设施 |
| [RabbitMqRecipientRegistrar](./com.euonia.bus.RabbitMqRecipientRegistrar.md) | class | 接收者注册器：为每个注册创建并启动 Consumer/Subscriber/Executor |
| [RabbitMqQueueConsumer](./com.euonia.bus.RabbitMqQueueConsumer.md) | class | 单播队列消费者（含 correlationId reply-to） |
| [RabbitMqTopicSubscriber](./com.euonia.bus.RabbitMqTopicSubscriber.md) | class | 多播 topic 订阅者（自动 ACK） |
| [RabbitMqRequestExecutor](./com.euonia.bus.RabbitMqRequestExecutor.md) | class | RPC 请求执行器（DeliverCallback） |
| [RabbitMqReplyType](./com.euonia.bus.RabbitMqReplyType.md) | enum | 回复类型：EXCEPTION, EMPTY, MESSAGE |

## 依赖

- `com.euonia:core` (compile)
- `com.euonia:pipeline` (compile)
- `com.euonia:bus-abstract` (compile)
- `com.euonia:bus-core` (compile)

## 作者

- damon (zhaorong@outlook.com)
