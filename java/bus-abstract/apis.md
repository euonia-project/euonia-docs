# Euonia Bus-Abstract 模块 API 文档

## 概述

Bus-Abstract 是 Euonia 消息总线的抽象契约层，定义了消息传输、分发、约定分类、策略路由和接收者注册的核心接口。该模块不包含任何具体传输实现，而是为 `bus-core`（编排层）和各传输适配器（`bus-inmemory`、`bus-rabbitmq`、`bus-kafka`）提供统一的扩展点。

- **Maven 坐标**: `com.euonia:bus-abstract`
- **Java 模块名**: `com.euonia.bus`
- **依赖**: `com.euonia:core`

## 导出包

### com.euonia.bus.annotation

消息分类、路由和订阅的注解。

| 类 | 类型 | 说明 |
|----|------|------|
| [@Channel](./com.euonia.bus.annotation.Channel.md) | annotation | 为消息类型指定默认通道 |
| [@DispatchIn](./com.euonia.bus.annotation.DispatchIn.md) | annotation | 指定消息的出站传输通道 |
| [@DistributedMessage](./com.euonia.bus.annotation.DistributedMessage.md) | annotation | 标记分布式传输消息 |
| [@Enqueue](./com.euonia.bus.annotation.Enqueue.md) | annotation | 指定队列名称和优先级 |
| [@LocalMessage](./com.euonia.bus.annotation.LocalMessage.md) | annotation | 标记本地传输消息 |
| [@Multicast](./com.euonia.bus.annotation.Multicast.md) | annotation | 标记为多播消息 |
| [@ReceiveIn](./com.euonia.bus.annotation.ReceiveIn.md) | annotation | 指定消息的入站传输通道 |
| [@Request](./com.euonia.bus.annotation.Request.md) | annotation | 标记为请求-响应消息 |
| [@Subscribe](./com.euonia.bus.annotation.Subscribe.md) | annotation | 标记消息处理器方法 |
| [@Unicast](./com.euonia.bus.annotation.Unicast.md) | annotation | 标记为单播消息 |

### com.euonia.bus.convention

消息约定分类，决定消息投递语义。

| 类 | 类型 | 说明 |
|----|------|------|
| [MessageConvention](./com.euonia.bus.convention.MessageConvention.md) | interface | 消息分类契约接口 |
| [MessageConventionBuilder](./com.euonia.bus.convention.MessageConventionBuilder.md) | class | 约定构建器，流式聚合多个约定 |
| [MessageConventionType](./com.euonia.bus.convention.MessageConventionType.md) | enum | 消息类型枚举：NONE, UNICAST, MULTICAST, REQUEST |

### com.euonia.bus.strategy

传输策略路由，决定消息走哪条通道。

| 类 | 类型 | 说明 |
|----|------|------|
| [TransportStrategy](./com.euonia.bus.strategy.TransportStrategy.md) | interface | 传输策略契约接口 |
| [TransportStrategyBuilder](./com.euonia.bus.strategy.TransportStrategyBuilder.md) | class | 策略构建器，流式聚合多个策略 |

### com.euonia.bus

核心抽象 — 传输、分发、上下文、信封和配置。

| 类 | 类型 | 说明 |
|----|------|------|
| [Transport](./com.euonia.bus.Transport.md) | interface | 传输抽象契约 |
| [Dispatcher](./com.euonia.bus.Dispatcher.md) | interface | 消息类型 → 传输名称的决策接口 |
| [Configurator](./com.euonia.bus.Configurator.md) | interface | 全局配置接口 |
| [MessageContext](./com.euonia.bus.MessageContext.md) | interface | 消息处理上下文 |
| [MessageContextBase](./com.euonia.bus.MessageContextBase.md) | class | 默认处理上下文实现 |
| [MessageEnvelope](./com.euonia.bus.MessageEnvelope.md) | interface | 消息信封接口 |
| [MessageHeaders](./com.euonia.bus.MessageHeaders.md) | class | 消息头常量定义 |
| [MessageMetadata](./com.euonia.bus.MessageMetadata.md) | class | 可扩展的元数据 Map |
| [HandlerContext](./com.euonia.bus.HandlerContext.md) | class | 处理器上下文 |
| [ChannelHandler](./com.euonia.bus.ChannelHandler.md) | interface | 通道处理器接口 |
| [ChannelRegistration](./com.euonia.bus.ChannelRegistration.md) | record | 通道注册记录 |

### com.euonia.bus.message

消息分类标记接口。

| 类 | 类型 | 说明 |
|----|------|------|
| [Message](./com.euonia.bus.message.Message.md) | interface | 消息基类标记接口 |
| [Unicast](./com.euonia.bus.message.Unicast.md) | interface | 单播消息标记 |
| [Multicast](./com.euonia.bus.message.Multicast.md) | interface | 多播消息标记 |
| [Request](./com.euonia.bus.message.Request.md) | interface | 请求-响应消息标记 |

### com.euonia.bus.event

消息处理事件体系。

| 类 | 类型 | 说明 |
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

消息总线异常层次。

| 类 | 类型 | 说明 |
|----|------|------|
| [ChannelNotRegisterException](./com.euonia.bus.exception.ChannelNotRegisterException.md) | exception | 通道未注册 |
| [MessageConventionException](./com.euonia.bus.exception.MessageConventionException.md) | exception | 约定异常 |
| [MessageDeliverException](./com.euonia.bus.exception.MessageDeliverException.md) | exception | 消息投递失败 |
| [MessageProcessingException](./com.euonia.bus.exception.MessageProcessingException.md) | exception | 消息处理失败 |
| [MessageTransportException](./com.euonia.bus.exception.MessageTransportException.md) | exception | 传输层错误 |
| [MessagePersistentException](./com.euonia.bus.exception.MessagePersistentException.md) | exception | 消息持久化失败 |
| [MessageTypeException](./com.euonia.bus.exception.MessageTypeException.md) | exception | 无效/未分类的消息类型 |

### com.euonia.bus.recipient

消息接收者角色定义。

| 类 | 类型 | 说明 |
|----|------|------|
| [Recipient](./com.euonia.bus.recipient.Recipient.md) | interface | 接收者基类 |
| [Consumer](./com.euonia.bus.recipient.Consumer.md) | interface | 通用消费者标记 |
| [Subscriber](./com.euonia.bus.recipient.Subscriber.md) | interface | 多播接收者 |
| [Executor](./com.euonia.bus.recipient.Executor.md) | interface | 单播/请求接收者 |
| [RecipientRegistrar](./com.euonia.bus.recipient.RecipientRegistrar.md) | interface | 接收者注册器 |

### com.euonia.bus.consistency

收件箱/发件箱模式（幂等消费与事务发件）抽象。

| 类 | 类型 | 说明 |
|----|------|------|
| [InboxEntry](./com.euonia.bus.consistency.InboxEntry.md) | class | 收件箱条目 |
| [InboxHandle](./com.euonia.bus.consistency.InboxHandle.md) | class | 收件箱处理句柄 |
| [InboxStore](./com.euonia.bus.consistency.InboxStore.md) | interface | 收件箱存储接口 |
| [OutboxEntry](./com.euonia.bus.consistency.OutboxEntry.md) | class | 发件箱条目 |
| [OutboxStore](./com.euonia.bus.consistency.OutboxStore.md) | interface | 发件箱存储接口 |
| [OutboxTransport](./com.euonia.bus.consistency.OutboxTransport.md) | interface | 发件箱传输接口 |

### com.euonia.bus.dlq

死信队列抽象。

| 类 | 类型 | 说明 |
|----|------|------|
| [DeadLetterMessage](./com.euonia.bus.dlq.DeadLetterMessage.md) | record | 死信消息 |

### com.euonia.bus.serialization

序列化契约。

| 类 | 类型 | 说明 |
|----|------|------|
| [MessageSerializer](./com.euonia.bus.serialization.MessageSerializer.md) | interface | 消息序列化契约 |

## 依赖

- `com.euonia:core` (compile)
- `org.junit.jupiter:junit-jupiter` (test)
- `org.assertj:assertj-core` (test)
