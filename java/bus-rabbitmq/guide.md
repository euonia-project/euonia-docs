# Bus-RabbitMQ 模块 — 开发者手册

> Euonia 消息总线的 RabbitMQ 传输适配器。基于 `bus-abstract` 的抽象契约，提供通过 RabbitMQ AMQP 代理的消息传递实现，支持单播队列、多播 topic 交换和请求-响应 RPC 模式。

- **Maven 坐标**: `com.euonia:bus-rabbitmq`
- **依赖**: `com.euonia:core`, `com.euonia:pipeline`, `com.euonia:bus-abstract`, `com.euonia:bus-core`
- **API文档**：[点击查看](./apis)

---

## 架构

```text
                    RabbitMqTransport
                  (实现 Transport 接口)
                            │
          ┌─────────────────┼─────────────────┐
          │                 │                 │
          ▼                 ▼                 ▼
  publishAsync        sendAsync         callAsync
  (fanout 交换器)     (直接队列)         (RPC 请求-响应)
          │                 │                 │
          ▼                 ▼                 ▼
  RabbitMqTopic       RabbitMqQueue      RabbitMqRequest
  Subscriber          Consumer           Executor
  (多播订阅者)         (单播消费者)        (RPC 执行器)
          │                 │                 │
          └─────────────────┼─────────────────┘
                            │
                            ▼
                  RabbitMqRecipient
              (抽象基类：事件监听/DLX)
                            │
                            ▼
              RabbitMqRecipientRegistrar
              (HandlerRegistration → Consumer/Subscriber/Executor)
```

---

## 核心概念

### RabbitMqTransport — AMQP 传输实现

实现 `Transport` 接口，带有 Failsafe 重试：

| 方法 | 交换器模式 | 说明 |
|------|-----------|------|
| `publishAsync` | fanout | 多播到所有订阅者 |
| `sendAsync` | direct queue | 单播到指定队列 |
| `callAsync` | RPC | 请求-响应，使用 `replyTo`/`correlationId` |

### RabbitMqRecipientRegistrar — 注册映射

将 `HandlerRegistration` 列表自动映射为 AMQP 组件：

| 消息类型 | 组件 | 模式 |
|----------|------|------|
| `Unicast` | `RabbitMqQueueConsumer` | 独占队列消费 |
| `Multicast` | `RabbitMqTopicSubscriber` | 自动 ACK fanout |
| `Request` | `RabbitMqRequestExecutor` | RPC `DeliverCallback` |

### RabbitMqBusOptions — 配置选项

| 字段 | 说明 |
|------|------|
| `host` / `port` | RabbitMQ 连接地址 |
| `username` / `password` | 认证凭据 |
| `exchangePrefix` / `queuePrefix` | 交换器/队列命名前缀 |
| `retryPolicy` | Failsafe 重试策略 |
| `useDlx` | 是否启用死信交换器 |

---

## 快速入门

```java
// 配置
var options = new RabbitMqBusOptions();
options.setHost("localhost");
options.setPort(5672);
options.setUsername("guest");
options.setPassword("guest");

// 创建传输
var transport = new RabbitMqTransport(options, handlerContext);

// 注册处理器
var registrar = new RabbitMqRecipientRegistrar(options, handlerContext);
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
    <artifactId>bus-rabbitmq</artifactId>
    <version>${euonia.version}</version>
</dependency>
```

## 作者

damon (zhaorong@outlook.com)
