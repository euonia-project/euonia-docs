# Euonia Bus-Kafka 模块 API 文档

## 概述

Euonia 消息总线的 Kafka 传输适配器。基于 `bus-abstract` 的抽象契约，提供通过 Apache Kafka 代理的消息传递实现，支持单播队列、多播 topic 订阅和请求-响应 RPC 模式。

- **Maven 坐标**: `com.euonia:bus-kafka`
- **Java 模块名**: `com.euonia.bus`
- **依赖**: `com.euonia:core`, `com.euonia:pipeline`, `com.euonia:bus-abstract`, `com.euonia:bus-core`

## 导出包

### com.euonia.bus

| 类 | 类型 | 说明 |
|----|------|------|
| [KafkaTransport](./com.euonia.bus.KafkaTransport.md) | class | Transport 接口的 Kafka 实现，含 Failsafe 重试 |
| [KafkaBusOptions](./com.euonia.bus.KafkaBusOptions.md) | class | Kafka 配置选项（bootstrap、topic、重试、producer/consumer 配置） |
| [KafkaConstants](./com.euonia.bus.KafkaConstants.md) | class | Kafka 内部常量（默认 topic 前缀、分区、复制因子） |
| [KafkaRecipient](./com.euonia.bus.KafkaRecipient.md) | abstract class | 接收者抽象基类，含事件监听器支持 |
| [KafkaRecipientRegistrar](./com.euonia.bus.KafkaRecipientRegistrar.md) | class | 接收者注册器：基于通道注册创建并启动 Kafka 消费者 |
| [KafkaQueueConsumer](./com.euonia.bus.KafkaQueueConsumer.md) | class | 单播队列消费者（轮询消息并发送回复） |
| [KafkaTopicSubscriber](./com.euonia.bus.KafkaTopicSubscriber.md) | class | 多播 topic 订阅者（pub/sub 模式） |
| [KafkaRequestExecutor](./com.euonia.bus.KafkaRequestExecutor.md) | class | RPC 请求执行器（request-response 模式） |

## 依赖

- `com.euonia:core` (compile)
- `com.euonia:pipeline` (compile)
- `com.euonia:bus-abstract` (compile)
- `com.euonia:bus-core` (compile)

## 作者

- damon (zhaorong@outlook.com)
