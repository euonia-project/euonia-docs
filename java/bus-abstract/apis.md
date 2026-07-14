# Euonia Bus-Abstract 模块 API 文档

## 概述

Bus-Abstract 是 Euonia 消息总线的抽象契约层，定义了消息传输、分发、约定分类、策略路由和接收者注册的核心接口。该模块不包含任何具体传输实现，而是为 `bus-core`（编排层）和各传输适配器（`bus-inmemory`、`bus-rabbitmq`、`bus-kafka`）提供统一的扩展点。

- **Maven 坐标**: `com.euonia:bus-abstract`
- **Java 模块名**: `com.euonia.bus`

## 导出包

### com.euonia.bus.annotation

消息分类、路由和订阅的注解，用于标记消息类型和处理器方法。

| 类名 | 类型 | 说明 |
|------|------|------|
| [Channel](./com.euonia.bus.annotation.Channel.md) | annotation | 指定消息处理器订阅的通道名称 |
| [DispatchIn](./com.euonia.bus.annotation.DispatchIn.md) | annotation | 指定消息的出站传输通道 |
| [DistributedMessage](./com.euonia.bus.annotation.DistributedMessage.md) | annotation | 标记消息应通过分布式传输（如 Kafka、RabbitMQ）发送 |
| [Enqueue](./com.euonia.bus.annotation.Enqueue.md) | annotation | 标记消息应入队等待处理，可指定队列名称和优先级 |
| [LocalMessage](./com.euonia.bus.annotation.LocalMessage.md) | annotation | 标记消息应通过本地传输（如内存）发送 |
| [Multicast](./com.euonia.bus.annotation.Multicast.md) | annotation | 标记消息为多播，发送给多个订阅者 |
| [ReceiveIn](./com.euonia.bus.annotation.ReceiveIn.md) | annotation | 指定消息的入站传输通道 |
| [Request](./com.euonia.bus.annotation.Request.md) | annotation | 标记消息为请求-响应，指定期望的响应类型 |
| [Subscribe](./com.euonia.bus.annotation.Subscribe.md) | annotation | 标记方法为消息订阅处理器，指定通道和分组 |
| [Unicast](./com.euonia.bus.annotation.Unicast.md) | annotation | 标记消息为单播，仅发送给一个订阅者 |

### com.euonia.bus.convention

消息约定分类，决定消息投递语义。

| 类名 | 类型 | 说明 |
|----|------|------|
| [MessageConvention](./com.euonia.bus.convention.MessageConvention.md) | interface | 消息分类契约接口 |
| [MessageConventionBuilder](./com.euonia.bus.convention.MessageConventionBuilder.md) | class | 约定构建器，流式聚合多个约定 |
| [MessageConventionType](./com.euonia.bus.convention.MessageConventionType.md) | enum | 消息类型枚举：NONE, UNICAST, MULTICAST, REQUEST |

### com.euonia.bus.strategy

传输策略路由，决定消息走哪条通道。

| 类名 | 类型 | 说明 |
|----|------|------|
| [TransportStrategy](./com.euonia.bus.strategy.TransportStrategy.md) | interface | 传输策略契约接口 |
| [TransportStrategyBuilder](./com.euonia.bus.strategy.TransportStrategyBuilder.md) | class | 策略构建器，流式聚合多个策略 |

### com.euonia.bus

核心抽象层 — 传输、分发、上下文、信封、元数据和通道处理。

| 类名 | 类型 | 说明 |
|------|------|------|
| [Transport](./com.euonia.bus.Transport.md) | interface | 传输抽象契约，定义消息发布、发送和请求-响应调用的方法 |
| [Dispatcher](./com.euonia.bus.Dispatcher.md) | interface | 消息类型到传输名称的决策接口 |
| [Configurator](./com.euonia.bus.Configurator.md) | interface | 全局配置接口 |
| [MessageContext](./com.euonia.bus.MessageContext.md) | interface | 消息处理上下文 |
| [MessageContextBase](./com.euonia.bus.MessageContextBase.md) | class | 消息上下文的默认实现 |
| [MessageEnvelope](./com.euonia.bus.MessageEnvelope.md) | interface | 消息信封接口，封装消息数据、元数据和头信息 |
| [MessageHeaders](./com.euonia.bus.MessageHeaders.md) | class | 消息头常量定义 |
| [MessageMetadata](./com.euonia.bus.MessageMetadata.md) | class | 可扩展的消息元数据键值对容器 |
| [HandlerContext](./com.euonia.bus.HandlerContext.md) | class | 消息处理器上下文 |
| [ChannelHandler](./com.euonia.bus.ChannelHandler.md) | record | 通道处理器，封装处理器类型、方法和实例 |
| [ChannelRegistration](./com.euonia.bus.ChannelRegistration.md) | class | 通道注册信息，包含消息类型和处理器列表 |

### com.euonia.bus.message

消息分类标记接口。

| 类名 | 类型 | 说明 |
|----|------|------|
| [Message](./com.euonia.bus.message.Message.md) | interface | 消息基类标记接口 |
| [Unicast](./com.euonia.bus.message.Unicast.md) | interface | 单播消息标记 |
| [Multicast](./com.euonia.bus.message.Multicast.md) | interface | 多播消息标记 |
| [Request](./com.euonia.bus.message.Request.md) | interface | 请求-响应消息标记 |

### com.euonia.bus.event

消息处理事件体系。

| 类名 | 类型 | 说明 |
|----|------|------|
| [MessageProcessedEvent](./com.euonia.bus.event.MessageProcessedEvent.md) | class | 基础事件 |
| [MessageDeliveredEvent](./com.euonia.bus.event.MessageDeliveredEvent.md) | class | 消息已投递 |
| [MessageReceivedEvent](./com.euonia.bus.event.MessageReceivedEvent.md) | class | 消息已接收 |
| [MessageAcknowledgedEvent](./com.euonia.bus.event.MessageAcknowledgedEvent.md) | class | 消息已确认 |
| [MessageRepliedEvent](./com.euonia.bus.event.MessageRepliedEvent.md) | class | 消息已回复 |
| [MessageHandledEvent](./com.euonia.bus.event.MessageHandledEvent.md) | class | 消息已处理 |
| [MessageSubscribedEvent](./com.euonia.bus.event.MessageSubscribedEvent.md) | class | 订阅事件 |
| [MessageProcessType](./com.euonia.bus.event.MessageProcessType.md) | enum | 处理类型枚举 |

### com.euonia.bus.exception

消息总线异常层次结构。

| 类名 | 类型 | 说明 |
|------|------|------|
| [ChannelNotRegisterException](./com.euonia.bus.exception.ChannelNotRegisterException.md) | exception | 通道未注册异常 |
| [MessageConventionException](./com.euonia.bus.exception.MessageConventionException.md) | exception | 消息约定异常 |
| [MessageDeliverException](./com.euonia.bus.exception.MessageDeliverException.md) | exception | 消息投递失败异常 |
| [MessageProcessingException](./com.euonia.bus.exception.MessageProcessingException.md) | exception | 消息处理失败异常 |
| [MessageTransportException](./com.euonia.bus.exception.MessageTransportException.md) | exception | 传输层错误异常 |
| [MessagePersistentException](./com.euonia.bus.exception.MessagePersistentException.md) | exception | 消息持久化失败异常 |
| [MessageTypeException](./com.euonia.bus.exception.MessageTypeException.md) | exception | 无效/未分类的消息类型异常 |

### com.euonia.bus.recipient

消息接收者角色定义。

| 类名 | 类型 | 说明 |
|----|------|------|
| [Recipient](./com.euonia.bus.recipient.Recipient.md) | interface | 接收者基类 |
| [Consumer](./com.euonia.bus.recipient.Consumer.md) | interface | 通用消费者标记 |
| [Subscriber](./com.euonia.bus.recipient.Subscriber.md) | interface | 多播接收者 |
| [Executor](./com.euonia.bus.recipient.Executor.md) | interface | 单播/请求接收者 |
| [RecipientRegistrar](./com.euonia.bus.recipient.RecipientRegistrar.md) | interface | 接收者注册器 |

### com.euonia.bus.consistency

收件箱/发件箱模式（幂等消费与事务发件）抽象。

| 类名 | 类型 | 说明 |
|----|------|------|
| [InboxEntry](./com.euonia.bus.consistency.InboxEntry.md) | class | 收件箱条目 |
| [InboxHandle](./com.euonia.bus.consistency.InboxHandle.md) | class | 收件箱处理句柄 |
| [InboxStore](./com.euonia.bus.consistency.InboxStore.md) | interface | 收件箱存储接口 |
| [OutboxEntry](./com.euonia.bus.consistency.OutboxEntry.md) | class | 发件箱条目 |
| [OutboxStore](./com.euonia.bus.consistency.OutboxStore.md) | interface | 发件箱存储接口 |
| [OutboxTransport](./com.euonia.bus.consistency.OutboxTransport.md) | interface | 发件箱传输接口 |

### com.euonia.bus.dlq

死信队列抽象。

| 类名 | 类型 | 说明 |
|----|------|------|
| [DeadLetterMessage](./com.euonia.bus.dlq.DeadLetterMessage.md) | record | 死信消息 |

### com.euonia.bus.serialization

序列化契约。

| 类名 | 类型 | 说明 |
|----|------|------|
| [MessageSerializer](./com.euonia.bus.serialization.MessageSerializer.md) | interface | 消息序列化契约 |

## 依赖

- `com.euonia:core` (compile)
- `org.junit.jupiter:junit-jupiter` (test)
- `org.assertj:assertj-core` (test)
