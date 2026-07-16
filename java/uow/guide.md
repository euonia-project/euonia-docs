# Unit of Work 模块 — 开发者手册

> 轻量级异步工作单元抽象层，用于在单个原子操作中协调事务资源（数据库、消息代理等）。受 .NET `Euonia.Uow` 模块启发。

- **Maven 坐标**: `com.euonia:unit-of-work`
- **依赖**: `com.euonia:core`
- **API文档**：[点击查看](./apis.md)

---

## 架构

```text
UnitOfWorkManager
        │
        ├── begin(options, requiresNew)
        │       │
        │       ▼
        │   ┌─────────────────────┐
        │   │    UnitOfWork        │
        │   │  (implements        │
        │   │   AutoCloseable)    │
        │   └────────┬────────────┘
        │            │
        │            ├── contexts: Map<String, UnitOfWorkContext>
        │            │       ├── "db"     → JdbcTransactionContext
        │            │       ├── "mq"     → MessageQueueContext
        │            │       └── "cache"  → CacheContext
        │            │
        │            ├── listeners
        │            │       ├── completedListeners
        │            │       ├── failedListeners
        │            │       └── disposedListeners
        │            │
        │            └── handlers
        │                    └── completedHandlers (async pre-completion)
        │
        └── getCurrent() → UnitOfWorkAccessor (ThreadLocal)
```

---

## 生命周期

```
initialize(options)
        │
        ▼
   [add contexts & business logic]
        │
        ├── completeAsync()
        │       │
        │       ├── saveChangesAsync()  ← flush all contexts
        │       ├── invokeCompletedHandlers()
        │       └── notifyCompleted()   ← fire completed listeners
        │
        └── close()  (AutoCloseable / try-with-resources)
                │
                ├── close all contexts
                ├── notifyFailed() if !completed
                └── notifyDisposed()
```

---

## 快速入门

### 编程式 API

```java
UnitOfWorkManager manager = new UnitOfWorkManager();

try (UnitOfWork uow = manager.begin(new UnitOfWorkOptions(true), false)) {
    uow.addContext("db", new JdbcTransactionContext(connection));

    uow.addCompletedListener(event ->
        log.info("Unit of work {} completed", event.getUnitOfWork().getId()));

    uow.addFailedListener(event ->
        log.error("Unit of work failed", event.getException()));

    // ... business logic ...

    uow.completeAsync().toCompletableFuture().join();
}
```

### 注解驱动（需 AOP，如 Spring 模块）

```java
import com.euonia.uow.annotation.UnitOfWork;

@Service
public class OrderService {

    @UnitOfWork
    public Order createOrder(CreateOrderCommand cmd) {
        // 方法执行前自动 begin()
        // 方法执行后自动 completeAsync()
        // 异常时自动触发 onFailure()
    }

    @UnitOfWork(disabled = true)
    public Order readOnlyQuery(Long id) {
        // 禁用工作单元，即使类级别声明了 @UnitOfWork
    }
}
```

### 嵌套工作单元

```java
try (UnitOfWork outer = manager.begin(options, false)) {
    outer.addContext("db", dbContext);

    // 嵌套工作单元不开启新事务，委托给父级
    try (UnitOfWork inner = manager.begin(options, false)) {
        // inner is a ChildUnitOfWork, delegates to outer
    }

    outer.completeAsync().join();
}
```

### 强制新事务

```java
// requiresNew=true 创建独立工作单元
try (UnitOfWork independent = manager.begin(options, true)) {
    // independent transaction, not nested
}
```

---

## Maven

```xml
<dependency>
    <groupId>com.euonia</groupId>
    <artifactId>unit-of-work</artifactId>
    <version>${euonia.version}</version>
</dependency>
```

## 依赖

- `com.euonia:core` (compile)

## 作者

damon (zhaorong@outlook.com)
