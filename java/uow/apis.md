# Euonia Unit of Work 模块 API 文档

## 概述

轻量级异步工作单元抽象层，用于在单个原子操作中协调事务资源（数据库、消息代理等）。受 .NET `Euonia.Uow` 模块启发。

- **Maven 坐标**: `com.euonia:unit-of-work`
- **Java 模块名**: `com.euonia.uow`
- **依赖**: `com.euonia:core`

## 导出包

### com.euonia.uow

工作单元核心实现。

| 类 | 类型 | 说明 |
|----|------|------|
| [UnitOfWork](./com.euonia.uow.UnitOfWork.md) | class | 协调 contexts、listeners 和生命周期（save → complete → dispose） |
| [UnitOfWorkManager](./com.euonia.uow.UnitOfWorkManager.md) | class | 入口点 — 创建工作单元，通过 ThreadLocal 管理环境作用域 |
| [UnitOfWorkAccessor](./com.euonia.uow.UnitOfWorkAccessor.md) | class | 当前环境工作单元的 ThreadLocal 持有者 |
| [ChildUnitOfWork](./com.euonia.uow.ChildUnitOfWork.md) | class | 嵌套时委托给父级（不开启新事务） |
| [UnitOfWorkOptions](./com.euonia.uow.UnitOfWorkOptions.md) | class | 事务标志、隔离级别、超时配置 |
| [UnitOfWorkContext](./com.euonia.uow.UnitOfWorkContext.md) | interface | 事务资源接口（save、commit、rollback、close） |
| [UnitOfWorkEnabled](./com.euonia.uow.UnitOfWorkEnabled.md) | interface | 标记接口，用于自动拦截 |
| [UnitOfWorkEvent](./com.euonia.uow.UnitOfWorkEvent.md) | class | 工作单元事件 |
| [UnitOfWorkFailure](./com.euonia.uow.UnitOfWorkFailure.md) | class | 工作单元失败事件 |
| [UnitOfWorkHelper](./com.euonia.uow.UnitOfWorkHelper.md) | class | 注解内省的静态工具类 |
| [UnitOfWorkIsolationLevel](./com.euonia.uow.UnitOfWorkIsolationLevel.md) | enum | 事务隔离级别 |

### com.euonia.uow.annotation

| 类 | 类型 | 说明 |
|----|------|------|
| [@UnitOfWork](./com.euonia.uow.annotation.UnitOfWork.md) | annotation | 声明式工作单元边界注解 |

## 依赖

- `com.euonia:core` (compile)
- `org.junit.jupiter:junit-jupiter` (test)

## 作者

- damon (zhaorong@outlook.com)
