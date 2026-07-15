# Euonia Bus-Core 模块 API 文档

## 概述

Bus-Core 是 Euonia 消息总线的编排引擎层。在 `bus-abstract` 定义的抽象契约之上，提供消息总线运行时实现（`MessageBus`），包括分发决策、处理器注册与调用、消息约定与策略配置、管道行为集成和自动处理器发现。

- **Maven 坐标**: `com.euonia:bus-core`
- **Java 模块名**: `com.euonia.bus`
- **依赖**: `com.euonia:core`, `com.euonia:pipeline`, `com.euonia:bus-abstract`

## 导出包

### com.euonia.bus

消息总线核心编排类。

| 类 | 类型 | 说明 |
|----|------|------|
| [Bus](./com.euonia.bus.Bus.md) | interface | 消息总线接口，定义 publish/send/call 三种投递模式 |
| [MessageBus](./com.euonia.bus.MessageBus.md) | class | 总线核心实现，协调分发、管道、传输全流程 |
| [Handler](./com.euonia.bus.Handler.md) | @FunctionalInterface | 类型化消息处理器 |
| [LambdaHandler](./com.euonia.bus.LambdaHandler.md) | interface | Lambda 风格处理器 |
| [DefaultConfigurator](./com.euonia.bus.DefaultConfigurator.md) | class | 配置中枢，聚合约定/策略/注册 |
| [DefaultHandlerContext](./com.euonia.bus.DefaultHandlerContext.md) | class | 默认处理器上下文（注册+调用） |
| [HandlerRegistration](./com.euonia.bus.HandlerRegistration.md) | record | 处理器注册元组 |
| [StrategicDispatcher](./com.euonia.bus.StrategicDispatcher.md) | class | 策略分发器，消息类型→传输名映射 |
| [ChannelRegistrar](./com.euonia.bus.ChannelRegistrar.md) | class | 通道注册器 |
| [MessageHandlerFinder](./com.euonia.bus.MessageHandlerFinder.md) | class | 处理器发现（@Subscribe / Handler 接口） |
| [RoutedMessage](./com.euonia.bus.RoutedMessage.md) | class | 完整传输消息封装 |

### com.euonia.bus.behavior

管道行为实现，在消息处理流程中插入横切关注点。

| 类 | 类型 | 说明 |
|----|------|------|
| [IncomingLoggingBehavior](./com.euonia.bus.behavior.IncomingLoggingBehavior.md) | class | 入站消息日志行为 |
| [OutgoingLoggingBehavior](./com.euonia.bus.behavior.OutgoingLoggingBehavior.md) | class | 出站消息日志行为 |

### com.euonia.bus.builder

消息投递的流式构建器。

| 类 | 类型 | 说明 |
|----|------|------|
| [PublishBuilder](./com.euonia.bus.builder.PublishBuilder.md) | class | 发布模式构建器 |
| [SendBuilder](./com.euonia.bus.builder.SendBuilder.md) | class | 发送模式构建器 |
| [CallBuilder](./com.euonia.bus.builder.CallBuilder.md) | class | 调用（请求-响应）模式构建器 |

### com.euonia.bus.convention

消息约定实现。

| 类 | 类型 | 说明 |
|----|------|------|
| [AnnotationMessageConvention](./com.euonia.bus.convention.AnnotationMessageConvention.md) | class | 基于注解的消息约定 |
| [BaseMessageConvention](./com.euonia.bus.convention.BaseMessageConvention.md) | class | 约定组合引擎（聚合多个约定） |
| [DefaultMessageConvention](./com.euonia.bus.convention.DefaultMessageConvention.md) | class | 基于标记接口的默认约定 |
| [DefaultMessageConventionBuilder](./com.euonia.bus.convention.DefaultMessageConventionBuilder.md) | class | 默认约定构建器 |
| [OverridableMessageConvention](./com.euonia.bus.convention.OverridableMessageConvention.md) | class | 可覆写约定装饰器 |

### com.euonia.bus.strategy

传输策略实现。

| 类 | 类型 | 说明 |
|----|------|------|
| [AnnotationTransportStrategy](./com.euonia.bus.strategy.AnnotationTransportStrategy.md) | class | 基于 @DispatchIn/@ReceiveIn 注解的策略 |
| [BaseTransportStrategy](./com.euonia.bus.strategy.BaseTransportStrategy.md) | class | 策略组合引擎 |
| [DefaultTransportStrategy](./com.euonia.bus.strategy.DefaultTransportStrategy.md) | class | 默认策略（中性） |
| [DefaultTransportStrategyBuilder](./com.euonia.bus.strategy.DefaultTransportStrategyBuilder.md) | class | 默认策略构建器 |
| [DistributedMessageTransportStrategy](./com.euonia.bus.strategy.DistributedMessageTransportStrategy.md) | class | 匹配 @DistributedMessage 的策略 |
| [LocalMessageTransportStrategy](./com.euonia.bus.strategy.LocalMessageTransportStrategy.md) | class | 匹配 @LocalMessage 的策略 |
| [OverridableTransportStrategy](./com.euonia.bus.strategy.OverridableTransportStrategy.md) | class | 可覆写策略装饰器 |

### com.euonia.bus.options

消息投递选项。

| 类 | 类型 | 说明 |
|----|------|------|
| [ExtendableOptions](./com.euonia.bus.options.ExtendableOptions.md) | abstract class | 可扩展选项基类 |
| [PublishOptions](./com.euonia.bus.options.PublishOptions.md) | class | 发布选项 |
| [SendOptions](./com.euonia.bus.options.SendOptions.md) | class | 发送选项 |
| [CallOptions](./com.euonia.bus.options.CallOptions.md) | class | 调用选项 |

## 依赖

- `com.euonia:core` (compile)
- `com.euonia:pipeline` (compile)
- `com.euonia:bus-abstract` (compile)
- `org.junit.jupiter:junit-jupiter` (test)
- `org.assertj:assertj-core` (test)

## 作者

- damon (zhaorong@outlook.com)
