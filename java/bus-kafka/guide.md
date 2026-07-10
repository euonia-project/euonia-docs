# Bus-Kafka 模块 — 开发者手册

> Euonia 消息总线的 Kafka 传输适配器。基于 `bus-abstract` 的抽象契约，提供通过 Apache Kafka 代理的消息传递实现，支持单播队列、多播 topic 订阅和请求-响应 RPC 模式。

- **Maven 坐标**: `com.euonia:bus-kafka`
- **依赖**: `com.euonia:core`, `com.euonia:pipeline`, `com.euonia:bus-abstract`, `com.euonia:bus-core`
- **API文档**：[点击查看](./apis)

---

## 架构

```text
                       KafkaTransport
                  (实现 Transport 接口)
                            │
          ┌─────────────────┼─────────────────┐
          │                 │                 │
          ▼                 ▼                 ▼
  publishAsync        sendAsync         callAsync
  (topic 发布)        (partition 队列)   (RPC 请求-响应)
          │                 │                 │
          ▼                 ▼                 ▼
  KafkaTopic          KafkaQueue         KafkaRequest
  Subscriber          Consumer           Executor
  (多播订阅者)         (单播消费者)        (RPC 执行器)
          │                 │                 │
          └─────────────────┼─────────────────┘
                            │
                            ▼
                    KafkaRecipient
              (抽象基类：事件监听)
                            │
                            ▼
              KafkaRecipientRegistrar
              (HandlerRegistration → Consumer/Subscriber/Executor)
```

---

## 核心概念

### KafkaTransport — Kafka 传输实现

实现 `Transport` 接口，带有 Failsafe 重试：

| 方法 | 模式 | 说明 |
|------|------|------|
| `publishAsync` | topic publish | 多播到所有 topic 订阅者 |
| `sendAsync` | partition queue | 单播到指定分区 |
| `callAsync` | RPC | 请求-响应模式 |

### KafkaRecipientRegistrar — 注册映射

| 消息类型 | 组件 | 模式 |
|----------|------|------|
| `Unicast` | `KafkaQueueConsumer` | 独占分区消费 |
| `Multicast` | `KafkaTopicSubscriber` | topic 订阅（pub/sub） |
| `Request` | `KafkaRequestExecutor` | RPC 请求-响应 |

### KafkaBusOptions — 配置选项

| 字段 | 说明 |
|------|------|
| `bootstrapServers` | Kafka broker 地址列表 |
| `topicPrefix` | topic 命名前缀 |
| `partitions` | 默认分区数 |
| `replicationFactor` | 默认复制因子 |
| `retryPolicy` | Failsafe 重试策略 |
| `producerConfig` / `consumerConfig` | 自定义 producer/consumer 配置 |

---

## 快速入门

```java
// 配置
var options = new KafkaBusOptions();
options.setBootstrapServers("localhost:9092");
options.setTopicPrefix("euonia");

// 创建传输
var transport = new KafkaTransport(options, handlerContext);

// 注册处理器
var registrar = new KafkaRecipientRegistrar(options, handlerContext);
registrar.register(handlerRegistrations);

// 发送消息
transport.sendAsync(routedMessage)
    .toCompletableFuture()
    .join();
```

---

## Maven

```xml
<dependency>
    <groupId>com.euonia</groupId>
    <artifactId>bus-kafka</artifactId>
    <version>${euonia.version}</version>
</dependency>
```

## 作者

damon (zhaorong@outlook.com)
