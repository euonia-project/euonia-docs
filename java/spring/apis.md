# Euonia Spring 模块 API 文档

## 概述

Spring 集成模块，为 Euonia 各核心模块提供 Spring Boot 自动配置和 Bean 注册，包括 `ServiceProvider`、`Pipeline`、`MessageBus`、`OSBA`、`HttpContextAccessor` 和 `UnitOfWork` 的 Spring 集成。

- **Maven 坐标**: `com.euonia:spring`
- **Java 模块名**: `com.euonia.spring`
- **依赖**: `com.euonia:core`, `com.euonia:osba`, `com.euonia:pipeline`, `com.euonia:bus-core`, `com.euonia:uow`, `org.springframework`

## 导出包

### com.euonia.reflection

Spring 集成核心：ApplicationContext 作为 ServiceProvider。

| 类 | 类型 | 说明 |
|----|------|------|
| [ApplicationContextServiceProvider](./com.euonia.reflection.ApplicationContextServiceProvider.md) | class | 基于 Spring ApplicationContext 的 ServiceProvider 实现 |
| [ServiceProviderConfiguration](./com.euonia.reflection.ServiceProviderConfiguration.md) | @Configuration | ServiceProvider Bean 注册 |

### com.euonia.bus

MessageBus Spring 自动配置。

| 类 | 类型 | 说明 |
|----|------|------|
| [MessageBusConfiguration](./com.euonia.bus.MessageBusConfiguration.md) | @Configuration | Bus + HandlerContext Bean 注册 |

### com.euonia.pipeline

Pipeline Spring 自动配置。

| 类 | 类型 | 说明 |
|----|------|------|
| [PipelineConfiguration](./com.euonia.pipeline.PipelineConfiguration.md) | @Configuration | PipelineFactory、Pipeline、PipelineDelegate Bean 注册（原型作用域） |

### com.euonia.osba

OSBA Spring 自动配置。

| 类 | 类型 | 说明 |
|----|------|------|
| [OsbaConfiguration](./com.euonia.osba.OsbaConfiguration.md) | @Configuration | ObjectFactory / BusinessObjectFactory Bean 注册 |

### com.euonia.http

HTTP 上下文 Spring 自动配置。

| 类 | 类型 | 说明 |
|----|------|------|
| [HttpContextAccessorConfiguration](./com.euonia.http.HttpContextAccessorConfiguration.md) | @Configuration | RequestContextAccessor Bean 注册 |

### com.euonia.uow

UoW Spring AOP 集成。

| 类 | 类型 | 说明 |
|----|------|------|
| [UnitOfWorkAspect](./com.euonia.uow.UnitOfWorkAspect.md) | @Aspect | `@UnitOfWork` 注解的环绕通知切面 |
| [UnitOfWorkAutoConfiguration](./com.euonia.uow.UnitOfWorkAutoConfiguration.md) | @Configuration | UoW Bean 注册 + @EnableAspectJAutoProxy |

### com.euonia.spring

Spring 常量。

| 类 | 类型 | 说明 |
|----|------|------|
| [BeanScope](./com.euonia.spring.BeanScope.md) | class | Spring Bean 作用域常量 |

## 依赖

- `com.euonia:core` (compile)
- `com.euonia:osba` (compile)
- `com.euonia:pipeline` (compile)
- `com.euonia:bus-core` (compile)
- `com.euonia:uow` (compile)
- `org.springframework` (compile)

## 作者

- damon (zhaorong@outlook.com)
