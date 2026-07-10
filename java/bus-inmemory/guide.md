# Bus-InMemory 模块 — 开发者手册

> Euonia 消息总线的进程内传输适配器。基于 `bus-abstract` 的抽象契约，提供无外部中间件的纯内存消息传递实现，适用于开发测试、单进程集成以及需要超低延迟的场景。

- **Maven 坐标**: `com.euonia:bus-inmemory`
- **依赖**: `com.euonia:core`, `com.euonia:pipeline`, `com.euonia:bus-abstract`, `com.euonia:bus-core`
- **API文档**：[点击查看](./apis)

---

## 架构

```text
                          InMemoryTransport
                    (实现 Transport 接口)
                                  │
                    ┌─────────────┼─────────────┐
                    │             │             │
                    ▼             ▼             ▼
            publishAsync    sendAsync     requestAsync
            (WeakRef 发送)  (StrongRef)   (sendAsync 包装)
                    │             │             │
                    └─────────────┼─────────────┘
                                  │
                                  ▼
                    ┌─────────────────────────┐
                    │       MessagePack        │
                    │  RoutedMessage + Context  │
                    └────────────┬────────────┘
                                 │
                    ┌────────────┴────────────┐
                    │                         │
                    ▼                         ▼
      ┌──────────────────────┐    ┌──────────────────────┐
      │ StrongReferenceMess. │    │ WeakReferenceMess.    │
      │  (单播 / 请求-响应)    │    │  (多播 / 发布-订阅)     │
      └──────────┬───────────┘    └──────────┬───────────┘
                 │                           │
                 ▼                           ▼
         InMemoryRecipient            InMemoryRecipient
                 │                           │
    ┌────────────┼────────────┐    ┌─────────┼─────────┐
    ▼            ▼            ▼    ▼         ▼         ▼
UnicastRec.  RequestRec.   MulticastRecipient
(Executor)  (Executor)     (Subscriber)
```

---

## 核心概念

### InMemoryTransport — 进程内传输实现

实现 `Transport` 接口，是整个模块的入口点。

| 方法 | 信使 | 异步模型 |
|------|------|----------|
| `publishAsync` | `WeakReferenceMessenger` | 发送后立即返回已完成 Future |
| `sendAsync` | `StrongReferenceMessenger` | 等待 `context.onReplied` 或 `complete` 事件 |
| `sendAsync(message, Class<R>)` | `StrongReferenceMessenger` | 从 reply 事件载荷转型为 `R` |
| `requestAsync` | `StrongReferenceMessenger` | 委托给 `sendAsync(message, Object.class)` |

**投递流程：**
1. 从 `RoutedMessage` 创建 `MessageContextBase`
2. 包装为 `MessagePack`（message + context + aborted 标志）
3. 通过对应信使发送至目标通道
4. 触发 `MessageDeliveredEvent` 监听器

### 信使引擎

| 信使 | 引用类型 | 用途 | 注册结构 |
|------|----------|------|----------|
| `StrongReferenceMessenger` | 强引用 | Unicast、Request | `ConcurrentMap<Class<?>, Map<String, Map<RecipientKey, Dispatcher>>>` |
| `WeakReferenceMessenger` | 弱引用 | Multicast | 同上，但使用 `WeakReference` 包装的 WeakKey |

**WeakReferenceMessenger 特性：**
- GC 语义：接收者无人持有强引用时自动退订
- 发送时跳过已被 GC 回收的接收者
- cleanup：扫描并移除已回收接收者的所有注册

### InMemoryRecipient — 接收者基类

接收流水线：
```text
receive(MessagePack)
  ├── 提取 RoutedMessage + MessageContext
  ├── 触发 MessageReceivedEvent
  ├── 调用 handleAsync(channel, payload, context, aborted)
  └── 触发 MessageAcknowledgedEvent
```

### 接收者注册映射

| 消息类型 | 接收者 | 信使 |
|----------|--------|------|
| `Unicast` | `InMemoryUnicastRecipient` | `StrongReferenceMessenger` |
| `Multicast` | `InMemoryMulticastRecipient` | `WeakReferenceMessenger` |
| `Request` | `InMemoryRequestRecipient` | `StrongReferenceMessenger` |

---

## 快速入门

```java
// 创建进程内传输
var transport = new InMemoryTransport(handlerContext);
transport.setConfigurator(configurator);

// 发送消息
transport.sendAsync(routedMessage)
    .toCompletableFuture()
    .join();

// 发布多播消息
transport.publishAsync(routedMessage)
    .toCompletableFuture()
    .join();
```

---

## Maven

```xml
<dependency>
    <groupId>com.euonia</groupId>
    <artifactId>bus-inmemory</artifactId>
    <version>${euonia.version}</version>
</dependency>
```

## 作者

damon (zhaorong@outlook.com)
