# Bus-Abstract 模块 — 开发者手册

> Euonia 消息总线的抽象契约层，定义了消息传输、分发、约定分类、策略路由和接收者注册的核心接口。该模块不包含任何具体传输实现，而是为 `bus-core`（编排层）和各传输适配器提供统一的扩展点。

- **Maven 坐标**: `com.euonia:bus-abstract`
- **依赖**: `com.euonia:core`
- **API文档**：[点击查看](./apis)

---

## 架构

```text
                        ┌─────────────────────────┐
                        │      Configurator         │  ← 全局约定、策略、处理器注册
                        └────────────┬────────────┘
                                     │
          ┌──────────────────────────┼──────────────────────────┐
          │                          │                          │
          ▼                          ▼                          ▼
┌─────────────────┐     ┌─────────────────────┐     ┌─────────────────────┐
│ MessageConvention│     │  TransportStrategy   │     │  HandlerRegistration │
│  (消息分类)       │     │  (传输策略路由)       │     │  (处理器元数据)       │
│                  │     │                      │     │                      │
│ unicast/multicast│     │ outgoing / incoming  │     │ channel + type       │
│ /request         │     │ local / distributed  │     │ + method             │
└────────┬────────┘     └──────────┬───────────┘     └─────────────────────┘
         │                         │
         ▼                         ▼
┌─────────────────┐     ┌─────────────────────┐
│    Dispatcher    │────▶│     Transport        │  ← publishAsync / sendAsync / requestAsync
│ (选择传输通道)    │     │   (抽象传输契约)      │
└─────────────────┘     └─────────────────────┘

                         ┌─────────────────────┐
                         │   RecipientRegistrar │  ← 将 HandlerRegistration 绑定到传输
                         └─────────────────────┘
                                     │
                          ┌──────────┴──────────┐
                          ▼                     ▼
                   ┌────────────┐       ┌────────────┐
                   │  Subscriber │       │  Executor   │
                   │ (多播接收者) │       │(单播/请求接收)│
                   └────────────┘       └────────────┘
```

Bus-Abstract 是契约层，提供三类核心抽象：**约定**（消息怎么投）、**策略**（走哪条通道）、**传输**（具体投递）。各传输适配器实现 `Transport`、`RecipientRegistrar` 等接口。

---

## 核心概念

### 约定（Convention）—— 消息类型分类

消息约定决定消息的投递语义：**单播**、**多播**还是**请求-响应**。支持两种分类方式：

| 分类方式 | 实现 | 说明 |
|---------|------|------|
| **接口标记** | `DefaultMessageConvention` | 消息类实现 `Unicast`、`Multicast`、`Request<R>` 接口 |
| **注解标记** | `AnnotationMessageConvention` | 消息类标注 `@Unicast`、`@Multicast`、`@Request` 注解 |

```java
// 方式一：接口标记
public class CreateOrderCommand implements Unicast { ... }
public class OrderCreatedEvent implements Multicast { ... }
public class GetOrderQuery implements Request<OrderDto> { ... }

// 方式二：注解标记
@Unicast
public class CreateOrderCommand { ... }
@Multicast
public class OrderCreatedEvent { ... }
@Request(responseType = OrderDto.class)
public class GetOrderQuery { ... }
```

| 类 / 接口 | 描述 |
|-----------|------|
| `MessageConvention` | 分类契约接口：`isUnicast(String)`、`isMulticast(String)`、`isRequest(String)` |
| `MessageConventionBuilder` | 流式构建器，聚合多个约定实例 |
| `MessageConventionType` | 枚举：`NONE`、`UNICAST`、`MULTICAST`、`REQUEST` |

### 策略（Strategy）—— 传输路由

传输策略决定消息的出站/入站传输选择。与约定正交：约定决定"怎么投"，策略决定"走哪条通道"。

| 类 / 接口 | 描述 |
|-----------|------|
| `TransportStrategy` | 策略契约：`outgoing()` / `incoming()` 返回消息类型匹配的传输名 |
| `TransportStrategyBuilder` | 流式构建器 |

相关注解驱动策略：

| 注解 | 说明 |
|------|------|
| `@DispatchIn` | 指定出站传输通道 |
| `@ReceiveIn` | 指定入站传输通道 |
| `@LocalMessage` | 标记本地传输消息 |
| `@DistributedMessage` | 标记分布式传输消息 |

### 传输（Transport）—— 抽象契约

`Transport` 接口是所有传输适配器的契约，`bus-core.MessageBus` 通过它完成实际的消息投递。

| 方法 | 说明 |
|------|------|
| `getName()` | 返回传输名称（如 `"inmemory"`、`"rabbitmq"`、`"kafka"`） |
| `publishAsync(RoutedMessage)` | 发布/多播消息 |
| `sendAsync(RoutedMessage)` | 单播消息（无响应） |
| `sendAsync(RoutedMessage, Class<R>)` | 单播消息，返回 `CompletableFuture<R>` |
| `requestAsync(RoutedMessage, Class<R>)` | 请求-响应，返回 `CompletableFuture<R>` |

### 消息信封（Envelope）

| 类 / 接口 | 描述 |
|-----------|------|
| `MessageEnvelope` | 信封接口：`messageId`、`correlationId`、`conversationId`、`requestTrackId`、`channel` |
| `MessageHeaders` | 消息头常量 |
| `MessageMetadata` | 可扩展的元数据 Map，带类型化读取方法 |

### 处理上下文（Context）

| 类 / 接口 | 描述 |
|-----------|------|
| `MessageContext` | 处理上下文抽象 — 提供消息访问、响应发送、失败通知、完成回调 |
| `MessageContextBase` | 默认实现 — 基于 `SubmissionPublisher` 的响应事件流 |

### 分发与注册

| 类 / 接口 | 描述 |
|-----------|------|
| `Dispatcher` | 消息类型 → 传输名称的决策接口 |
| `HandlerContext` | 处理器上下文 — 管理消息订阅监听器 |
| `Configurator` | 全局配置接口 — 暴露约定构建器、策略构建器、处理器注册列表 |
| `RecipientRegistrar` | 接收者注册器 — 将 `HandlerRegistration` 列表绑定到具体传输 |

### 接收者角色

| 接口 | 说明 |
|------|------|
| `Recipient` | 接收者基类（继承 `AutoCloseable`） |
| `Consumer` | 通用消费者标记接口 |
| `Subscriber` | 多播接收者 — 用于 `Multicast` 消息 |
| `Executor` | 单播/请求接收者 — 用于 `Unicast` 和 `Request` 消息 |

### 事件体系

| 类 | 描述 |
|----|------|
| `MessageProcessedEvent` | 基础事件 — 包含消息、上下文、处理类型 |
| `MessageDeliveredEvent` | 消息已投递 |
| `MessageReceivedEvent` | 消息已接收 |
| `MessageAcknowledgedEvent` | 消息已确认 |
| `MessageRepliedEvent` | 消息已回复 — 包含响应载荷 |
| `MessageHandledEvent` | 消息已处理 — 包含处理器类型 |
| `MessageSubscribedEvent` | 订阅元数据 |
| `MessageProcessType` | 处理类型枚举：`SEND`、`DELIVERED`、`RECEIVED`、`ACKNOWLEDGED`、`REPLIED`、`HANDLED` |

### 异常层次

| 异常类 | 说明 |
|--------|------|
| `ChannelNotRegisterException` | 通道未注册异常 |
| `MessageConventionException` | 消息约定异常 |
| `MessageDeliverException` | 消息投递失败 |
| `MessageProcessingException` | 消息处理失败 |
| `MessageTransportException` | 传输层错误 |
| `MessagePersistentException` | 消息持久化失败 |
| `MessageTypeException` | 无效/未分类的消息类型 |

### @Subscribe — 消息处理器标记

```java
@Subscribe(channel = "orders", group = "order-processor")
public void handleOrderCreated(OrderCreatedEvent event) {
    // 处理订单创建事件
}
```

### 收件箱与发件箱

| 模式 | 接口 | 说明 |
|------|------|------|
| **Inbox** | `InboxStore`、`InboxEntry`、`InboxHandle` | 幂等消费，防止重复处理 |
| **Outbox** | `OutboxStore`、`OutboxEntry`、`OutboxTransport` | 事务发件，确保消息与业务状态一致 |
| **DLQ** | `DeadLetterMessage` | 死信队列，处理失败消息 |

---

## 与其他模块的关系

```text
bus-abstract  (本模块 — 契约层)
    │
    ├──▶ bus-core      (编排层)   — 实现 Configurator、Dispatcher、HandlerContext；
    │                                MessageBus 使用 Transport、RoutedMessage、异常等
    │
    ├──▶ bus-inmemory  (传输适配器) — 实现 Transport、RecipientRegistrar、Subscriber、Executor
    ├──▶ bus-rabbitmq  (传输适配器) — 实现 Transport（骨架）
    └──▶ bus-kafka     (传输适配器) — 依赖声明，待实现
```

---

## 快速入门

### 添加依赖

```xml
<dependency>
    <groupId>com.euonia</groupId>
    <artifactId>bus-abstract</artifactId>
    <version>${revision}</version>
</dependency>
```

### 定义消息类型（接口方式）

```java
import com.euonia.bus.message.Unicast;
import com.euonia.bus.message.Multicast;
import com.euonia.bus.message.Request;

// 单播命令
public class CreateOrderCommand implements Unicast {
    private String orderId;
}

// 多播事件
public class OrderCreatedEvent implements Multicast {
    private String orderId;
}

// 请求-响应
public class GetOrderQuery implements Request<OrderDto> {
    private String orderId;
}
```

### 定义消息类型（注解方式）

```java
import com.euonia.bus.annotation.*;

@Unicast
@Channel("orders")
@DispatchIn(transports = {"rabbitmq"})
public class CreateOrderCommand { ... }

@Multicast
@DistributedMessage
public class OrderCreatedEvent { ... }
```

### 配置消息约定与策略

```java
import com.euonia.bus.convention.*;
import com.euonia.bus.strategy.*;

// 构建消息约定
MessageConvention convention = new MessageConventionBuilder()
    .add(new DefaultMessageConvention())       // 接口标记
    .add(new AnnotationMessageConvention())     // 注解标记
    .getConvention();

// 构建传输策略
TransportStrategy strategy = new TransportStrategyBuilder()
    .add(new AnnotationTransportStrategy())
    .add(new LocalMessageTransportStrategy())
    .add(new DistributedMessageTransportStrategy())
    .getStrategy();

// 判断消息类型
boolean isUnicast = convention.isUnicast("orders");     // true
boolean isMulticast = convention.isMulticast("events");  // true
boolean isRequest = convention.isRequest("queries");     // true
```

---

## 设计模式

| 模式 | 应用 |
|------|------|
| **策略模式** | `MessageConvention` 和 `TransportStrategy` 的多种实现 |
| **组合模式** | 约定和策略构建器聚合多个求值器 |
| **构建器模式** | `MessageConventionBuilder` 和 `TransportStrategyBuilder` |
| **装饰器模式** | 可覆写约定/策略包装器 |
| **标记接口 / 标记注解** | 双通道消息分类（`Unicast` / `@Unicast`） |
| **观察者模式** | `MessageContextBase` 通过 `SubmissionPublisher` 发布事件 |
| **信封模式** | `RoutedMessage` 携带载荷和传输元数据 |
| **注册表模式** | `Configurator` 存储策略构建器和处理器注册 |

---

## API 参考

### 导出包总览

| 包名 | 类数 | 说明 |
|------|------|------|
| `com.euonia.bus.annotation` | 10 | 消息分类、路由和订阅的注解 |
| `com.euonia.bus.convention` | 3 | 消息约定分类 |
| `com.euonia.bus.strategy` | 2 | 传输策略路由 |
| `com.euonia.bus` | 11 | 核心抽象：传输、分发、上下文、信封 |
| `com.euonia.bus.message` | 4 | 消息分类标记接口 |
| `com.euonia.bus.event` | 8 | 消息处理事件体系 |
| `com.euonia.bus.exception` | 7 | 异常层次 |
| `com.euonia.bus.recipient` | 5 | 消息接收者角色 |
| `com.euonia.bus.consistency` | 6 | 收件箱/发件箱模式抽象 |
| `com.euonia.bus.dlq` | 1 | 死信队列 |
| `com.euonia.bus.serialization` | 1 | 序列化契约 |

> 完整的 API 类级文档见 [apis.md](./apis.md) 及各独立类文档。

---

## Maven

```xml
<dependency>
    <groupId>com.euonia</groupId>
    <artifactId>bus-abstract</artifactId>
    <version>${euonia.version}</version>
</dependency>
```

## 依赖

- `com.euonia:core` (compile)
- `org.junit.jupiter:junit-jupiter` (test)
- `org.assertj:assertj-core` (test)
