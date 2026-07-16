# DDD 模块 — 开发者手册

> 领域驱动设计（Domain-Driven Design）—— Euonia 框架的战术设计工具箱。提供 Entity、Aggregate、ValueObject、Command、DomainEvent、UseCase 和 ApplicationService 等核心 DDD 构建块，帮助开发者以领域模型为中心构建高内聚、低耦合的业务系统。

- **Maven 坐标**: `com.euonia:domain-driven-design`
- **依赖**: `com.euonia:core`
- **API文档**：[点击查看](./apis)

---

## 架构

```text
┌──────────────────────────────────────────────────────────────────┐
│                       DDD 模块架构                               │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌────────── 领域层 ──────────┐  ┌────── 事件系统 ───────┐      │
│  │ Entity<ID>    Aggregate<I> │  │ Event ← DomainEvent   │      │
│  │ EntityBase<I> AggregateBase│  │ EventBase  DomainEvtB │      │
│  │ ValueObject<T>             │  │ EventAggregate        │      │
│  │ HasDomainEvents            │  │ ApplicationEvent      │      │
│  └────────────────────────────┘  └────────────────────────┘      │
│                                                                  │
│  ┌────────── 命令系统 ─────────┐  ┌────── 应用层 ──────────┐    │
│  │ Command ← CommandBase      │  │ ApplicationService     │    │
│  │                            │  │ BaseApplicationService │    │
│  └────────────────────────────┘  └────────────────────────┘     │
│                                                                  │
│  ┌────────── 用例层 ──────────────────────────────────────┐     │
│  │ UseCase<I,O>  UseCaseSuccess<O>  UseCaseFailure        │     │
│  │ UseCasePresenter<O> (Reactive Streams)                 │     │
│  └───────────────────────────────────────────────────────┘      │
│                                                                  │
│  ┌────────── 审计 ────────────────────────────────────────┐     │
│  │ @Audited  AuditRecord<ID>  AuditStore                  │     │
│  └───────────────────────────────────────────────────────┘      │
└──────────────────────────────────────────────────────────────────┘
```

---

## 核心概念

### 领域构建块

| 类 / 接口 | 描述 |
|-----------|------|
| `Entity<ID>` | 实体接口 — 定义具有唯一标识（ID）的领域对象，通过 `getId()` 和 `getKeys()` 表达身份 |
| `EntityBase<ID>` | 实体抽象基类 — 提供 `id` 属性的默认实现 |
| `Aggregate<ID>` | 聚合根标记接口 — 继承 `Entity<ID>`，表示该实体是聚合的根 |
| `AggregateBase<ID>` | 聚合根基类 — 扩展 `EntityBase`，内置领域事件管理和 `HasDomainEvents` 契约实现 |
| `ValueObject<T>` | 值对象基类 — 基于字段的 `equals`、`hashCode` 和 `compareTo` 实现 |

#### 实体

```java
public interface Entity<ID extends Comparable<ID>> {
    ID getId();
    void setId(ID id);
    default Object[] getKeys() { return new Object[]{getId()}; }
}
```

实体通过标识而非属性来区分彼此。

#### 聚合根

聚合是一组相关领域对象的集合，以聚合根为入口进行访问和修改。聚合根负责维护聚合内部的一致性。

```java
// 聚合根中注册事件处理器
registerEvent(OrderCreatedEvent.class, event -> {
    this.status = OrderStatus.CREATED;
});

// 触发领域事件
raiseEvent(new OrderCreatedEvent(orderId, amount));

// 获取所有未提交事件
List<DomainEvent> events = order.getEvents();
```

#### 值对象

```java
public class Money extends ValueObject<Money> {
    private final BigDecimal amount;
    private final String currency;
    // equals/hashCode/comparison auto-handled by ValueObject
}
```

值对象没有独立标识，通过属性值定义等价性。

---

### 事件系统

事件分为领域事件（`DomainEvent`）和应用事件（`ApplicationEvent`），均扩展自 `Event` 接口。

| 类 / 接口 | 描述 |
|-----------|------|
| `Event` | 事件基类接口 — `sequence`、`eventIntent`、`originatorType`、`originatorId` |
| `EventBase` | 事件抽象基类 — 基于 `HashMap` 的属性存储 |
| `DomainEvent` | 领域事件接口 — 可 `attach()` 到聚合根 |
| `DomainEventBase` | 领域事件基类 — `attach()` 自动设置来源信息 |
| `ApplicationEvent` | 应用事件标记接口 |
| `EventAggregate` | 事件元数据聚合 |

每个事件携带：`originatorType`、`originatorId`、`eventIntent`（默认为类名）、`sequence`。

---

### 命令系统

| 类 | 描述 |
|----|------|
| `Command` | 命令接口 — 命令对象的标记接口 |
| `CommandBase` | 命令抽象基类 — 基于 `HashMap` 的属性容器 |

命令对象封装操作意图和数据，由命令处理器执行，实现 CQRS 的命令侧。

---

### 用例层

```java
// 定义用例
public class CreateOrderUseCase implements UseCase<CreateOrderInput, OrderResult> {
    @Override
    public OrderResult execute(CreateOrderInput input) {
        // 业务逻辑
        return new OrderResult(...);
    }
}

// 使用展示器
var presenter = new UseCasePresenter<OrderResult>();
presenter.subscribe(
    result -> System.out.println("Success: " + result),
    error  -> System.err.println("Error: " + error.getMessage())
);

// 通知结果
presenter.success(orderResult);   // 或 presenter.error(exception);
```

| 接口 | 描述 |
|------|------|
| `UseCase<I,O>` | 用例接口 — `execute(I input): O` |
| `UseCaseSuccess<O>` | 成功输出端口 |
| `UseCaseFailure` | 失败输出端口 |
| `UseCasePresenter<O>` | 展示器，基于 `SubmissionPublisher` 的响应式订阅 |

---

### 应用服务

```java
public class OrderService extends BaseApplicationService {
    public OrderResult createOrder(CreateOrderCommand cmd) {
        // 获取用户
        UserPrincipal user = getUser();
        // 获取依赖
        OrderRepository repo = getService(OrderRepository.class).get();
        // 执行用例
        return new CreateOrderUseCase().execute(new CreateOrderInput(cmd));
    }
}
```

- `ApplicationService` — 应用服务标记接口
- `BaseApplicationService` — 内置 `ServiceProvider` 引用

---

### 审计

| 类 | 描述 |
|----|------|
| `@Audited` | 审计注解 — 可用于类型、字段、方法级别 |
| `AuditRecord<ID>` | 审计记录 — `entityName`、`entityId`、`action`、`timestamp`、`userId` |
| `AuditStore` | 审计存储接口 — `save(T record)` |

---

## 设计模式

| 模式 | 应用 |
|------|------|
| **实体-值对象** | `Entity` vs `ValueObject` — 标识等价 vs 属性等价 |
| **聚合模式** | `AggregateBase` 管理子实体一致性和领域事件 |
| **事件溯源** | `HasDomainEvents` + `raiseEvent` / `applyEvent` |
| **CQRS** | `Command` 命令对象封装操作意图，由处理器执行 |
| **端口-适配器** | `UseCaseSuccess` / `UseCaseFailure` 输出端口 |
| **观察者** | `UseCasePresenter` 使用 `SubmissionPublisher` |
| **模板方法** | `DomainEventBase.attach()` 自动设置来源信息 |

---

## 快速入门

### 添加依赖

```xml
<dependency>
    <groupId>com.euonia</groupId>
    <artifactId>domain-driven-design</artifactId>
    <version>${revision}</version>
</dependency>
```

### 定义实体和值对象

```java
// 值对象
public class Money extends ValueObject<Money> {
    private final BigDecimal amount;
    private final String currency;
    public Money(BigDecimal amount, String currency) { ... }
}

// 聚合根
public class Order extends AggregateBase<Long> {
    private Money total;
    private OrderStatus status;
    
    public Order(Long id) {
        setId(id);
        registerEvent(OrderCreatedEvent.class, e -> this.status = OrderStatus.CREATED);
    }
    
    public void create(Customer customer, Money total) {
        this.total = total;
        raiseEvent(new OrderCreatedEvent(getId(), total));
    }
}
```

### 定义命令和应用服务

```java
public class CreateOrderCommand extends CommandBase {
    // HashMap-based properties
}

public class OrderApplicationService extends BaseApplicationService {
    public void handle(CreateOrderCommand cmd) {
        var repo = getService(OrderRepository.class).get();
        var order = new Order(ObjectId.snowflake().getValue(Long.class));
        order.create(cmd.getCustomer(), cmd.getTotal());
        repo.save(order);
        // 领域事件可通过消息总线发布
        // order.getEvents().forEach(event -> eventBus.publish(event));
    }
}
```

---

## Maven

```xml
<dependency>
    <groupId>com.euonia</groupId>
    <artifactId>domain-driven-design</artifactId>
    <version>${revision}</version>
</dependency>
```

## 依赖

- `com.euonia:core` (compile)

## 作者

damon (zhaorong@outlook.com)
