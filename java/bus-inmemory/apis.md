# Euonia Bus-InMemory 模块 API 文档

## 概述

Euonia 消息总线的进程内传输适配器。基于 `bus-abstract` 的抽象契约，提供无外部中间件的纯内存消息传递实现，适用于开发测试、单进程集成以及需要超低延迟的场景。

- **Maven 坐标**: `com.euonia:bus-inmemory`
- **Java 模块名**: `com.euonia.bus`
- **依赖**: `com.euonia:core`, `com.euonia:pipeline`, `com.euonia:bus-abstract`, `com.euonia:bus-core`

## 导出包

### com.euonia.bus

进程内传输的核心实现类。

| 类 | 类型 | 说明 |
|----|------|------|
| [InMemoryTransport](./com.euonia.bus.InMemoryTransport.md) | class | Transport 接口的进程内实现 |
| [InMemoryBusOptions](./com.euonia.bus.InMemoryBusOptions.md) | class | 进程内总线配置选项 |
| [InMemoryRecipient](./com.euonia.bus.InMemoryRecipient.md) | abstract class | 接收者基类，实现消息处理流水线 |
| [InMemoryUnicastRecipient](./com.euonia.bus.InMemoryUnicastRecipient.md) | class | 单播接收者（Executor） |
| [InMemoryMulticastRecipient](./com.euonia.bus.InMemoryMulticastRecipient.md) | class | 多播接收者（Subscriber） |
| [InMemoryRequestRecipient](./com.euonia.bus.InMemoryRequestRecipient.md) | class | 请求-响应接收者（Executor） |
| [InMemoryRecipientRegistrar](./com.euonia.bus.InMemoryRecipientRegistrar.md) | class | 接收者注册映射器 |
| [InMemoryMessageDispatcher](./com.euonia.bus.InMemoryMessageDispatcher.md) | class | 消息分发器（单例） |
| [InMemoryDeadLetterQueue](./com.euonia.bus.InMemoryDeadLetterQueue.md) | class | 死信队列（单例，CopyOnWriteArrayList） |
| [MessagePack](./com.euonia.bus.MessagePack.md) | class | 传输信封包装 |

### com.euonia.bus.messenger

内部消息分发子系统。

| 类 | 类型 | 说明 |
|----|------|------|
| [Messenger](./com.euonia.bus.messenger.Messenger.md) | interface | 信使契约：register/send/unregister/cleanup/reset |
| [StrongReferenceMessenger](./com.euonia.bus.messenger.StrongReferenceMessenger.md) | class | 强引用信使（Unicast/Request） |
| [WeakReferenceMessenger](./com.euonia.bus.messenger.WeakReferenceMessenger.md) | class | 弱引用信使（Multicast，GC 友好） |
| [Recipient](./com.euonia.bus.messenger.Recipient.md) | @FunctionalInterface | 泛型消息接收者 |
| [MessageHandler](./com.euonia.bus.messenger.MessageHandler.md) | @FunctionalInterface | 类型化处理器 |
| [MessageHandlerDispatcher](./com.euonia.bus.messenger.MessageHandlerDispatcher.md) | abstract class | 处理器分发器 |
| [EquatableType](./com.euonia.bus.messenger.EquatableType.md) | class | 不可变 (message, token) 复合键 |
| [MessengerReferenceType](./com.euonia.bus.messenger.MessengerReferenceType.md) | enum | STRONG / WEAK |

## 依赖

- `com.euonia:core` (compile)
- `com.euonia:pipeline` (compile)
- `com.euonia:bus-abstract` (compile)
- `com.euonia:bus-core` (compile)

## 作者

- damon (zhaorong@outlook.com)
