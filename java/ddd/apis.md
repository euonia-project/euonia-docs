# Euonia DDD 模块 API 文档

## 概述

领域驱动设计（Domain-Driven Design）—— Euonia 框架的战术设计工具箱。提供 Entity、Aggregate、ValueObject、Command、DomainEvent、UseCase 和 ApplicationService 等核心 DDD 构建块，帮助开发者以领域模型为中心构建高内聚、低耦合的业务系统。

- **Maven 坐标**: `com.euonia:domain-driven-design`
- **Java 模块名**: `com.euonia.domain`
- **依赖**: `com.euonia:core`, `com.euonia:pipeline`, `com.euonia:unit-of-work`, `com.euonia:bus-core`

## 导出包

### com.euonia.domain

领域层核心构建块。

| 类 | 类型 | 说明 |
|----|------|------|
| [Entity](./com.euonia.domain.Entity.md) | interface | 实体接口，定义具有唯一标识的领域对象 |
| [EntityBase](./com.euonia.domain.EntityBase.md) | abstract class | 实体抽象基类，提供 id 属性默认实现 |
| [Aggregate](./com.euonia.domain.Aggregate.md) | interface | 聚合根标记接口 |
| [AggregateBase](./com.euonia.domain.AggregateBase.md) | abstract class | 聚合根基类，内置领域事件管理 |
| [ValueObject](./com.euonia.domain.ValueObject.md) | class | 值对象基类，基于字段的 equals/hashCode/compareTo |
| [HasDomainEvents](./com.euonia.domain.HasDomainEvents.md) | interface | 领域事件契约接口 |

### com.euonia.domain.event

事件系统。

| 类 | 类型 | 说明 |
|----|------|------|
| [Event](./com.euonia.domain.event.Event.md) | interface | 事件基类接口 |
| [EventBase](./com.euonia.domain.event.EventBase.md) | abstract class | 事件抽象基类，基于 HashMap 的属性存储 |
| [DomainEvent](./com.euonia.domain.event.DomainEvent.md) | interface | 领域事件接口 |
| [DomainEventBase](./com.euonia.domain.event.DomainEventBase.md) | abstract class | 领域事件基类，自动设置来源信息 |
| [ApplicationEvent](./com.euonia.domain.event.ApplicationEvent.md) | interface | 应用事件标记接口 |
| [ApplicationEventBase](./com.euonia.domain.event.ApplicationEventBase.md) | abstract class | 应用事件基类 |
| [EventAggregate](./com.euonia.domain.event.EventAggregate.md) | class | 事件元数据聚合 |

### com.euonia.domain.command

命令系统。

| 类 | 类型 | 说明 |
|----|------|------|
| [Command](./com.euonia.domain.command.Command.md) | interface | 命令接口，扩展 Unicast |
| [CommandBase](./com.euonia.domain.command.CommandBase.md) | abstract class | 命令抽象基类，基于 HashMap 的属性容器 |

### com.euonia.domain.auditing

审计系统。

| 类 | 类型 | 说明 |
|----|------|------|
| [@Audited](./com.euonia.domain.auditing.Audited.md) | annotation | 审计注解 |
| [AuditRecord](./com.euonia.domain.auditing.AuditRecord.md) | class | 审计记录实体（extends EntityBase），记录 entityName/entityId/action/timestamp/userId |
| [AuditStore](./com.euonia.domain.auditing.AuditStore.md) | interface | 审计存储接口 |

### com.euonia.application

应用服务层。

| 类 | 类型 | 说明 |
|----|------|------|
| [ApplicationService](./com.euonia.application.ApplicationService.md) | interface | 应用服务标记接口 |
| [BaseApplicationService](./com.euonia.application.BaseApplicationService.md) | abstract class | 应用服务基类，内置 ServiceProvider 和 Bus |

### com.euonia.usecase

用例层。

| 类 | 类型 | 说明 |
|----|------|------|
| [UseCase](./com.euonia.usecase.UseCase.md) | interface | 用例接口 |
| [UseCaseSuccess](./com.euonia.usecase.UseCaseSuccess.md) | interface | 成功输出端口 |
| [UseCaseFailure](./com.euonia.usecase.UseCaseFailure.md) | interface | 失败输出端口 |
| [UseCasePresenter](./com.euonia.usecase.UseCasePresenter.md) | class | 用例展示器，基于 SubmissionPublisher 的响应式订阅 |

## 依赖

- `com.euonia:core` (compile)
- `org.junit.jupiter:junit-jupiter` (test)
- `org.assertj:assertj-core` (test)

## 作者

- damon (zhaorong@outlook.com)
