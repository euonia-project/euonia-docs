# Euonia Core 模块 API 文档

## 概述

`euonia-core` 模块是 Euonia 框架的核心基础模块，提供了一套通用工具类和基础设施组件，
涵盖注解验证、对象池管理、唯一 ID 生成、HTTP 异常模型、反射工具、安全基础类型、元组以及字符串/对象工具等功能。

- **Maven 坐标**: `com.euonia:core`
- **Java 模块名**: `com.euonia.core`

## 导出包

| 包名 | 说明 |
|------|------|
| `com.euonia.annotation` | 自定义验证注解及验证器实现 |
| `com.euonia.core` | 核心工具类：对象池、ID 生成器、优先级队列等 |
| `com.euonia.http` | HTTP 异常模型与请求上下文抽象 |
| `com.euonia.reflection` | 反射工具：类扫描、服务提供、泛型类型处理 |
| `com.euonia.security` | 安全相关：认证异常、用户主体模型 |
| `com.euonia.tuple` | 元组类型：Solo ~ Decet（1 到 10 元素） |
| `com.euonia.utility` | 通用工具类：断言、对象反射、字符串操作 |

## 包详情

### com.euonia.annotation

验证注解与验证器框架。通过 `@Validation` 元注解将验证器关联到注解上，
在运行时对字段或方法参数进行约束校验。

| 类 | 类型 | 说明 |
|----|------|------|
| [@Range](./com.euonia.annotation.Range.md) | 注解 | 数值范围约束 |
| [RangeValidator](./com.euonia.annotation.RangeValidator.md) | 验证器 | 数值范围验证逻辑 |
| [@RegularExpression](./com.euonia.annotation.RegularExpression.md) | 注解 | 正则表达式约束 |
| [RegularExpressionValidator](./com.euonia.annotation.RegularExpressionValidator.md) | 验证器 | 正则匹配验证逻辑 |
| [@Required](./com.euonia.annotation.Required.md) | 注解 | 必填项约束 |
| [RequiredValidator](./com.euonia.annotation.RequiredValidator.md) | 验证器 | 非空验证逻辑 |
| [@StringLength](./com.euonia.annotation.StringLength.md) | 注解 | 字符串长度约束 |
| [StringLengthValidator](./com.euonia.annotation.StringLengthValidator.md) | 验证器 | 字符串长度验证逻辑 |
| [@Validation](./com.euonia.annotation.Validation.md) | 元注解 | 关联验证器类 |
| [Validator](./com.euonia.annotation.Validator.md) | 接口 | 通用验证器接口 |

### com.euonia.core

核心基础设施组件，包括对象池、多种 ID 生成策略和优先级队列。

| 类 | 类型 | 说明 |
|----|------|------|
| [DefaultObjectPool](./com.euonia.core.DefaultObjectPool.md) | 类 | 通用对象池实现 |
| [DefaultObjectPoolProvider](./com.euonia.core.DefaultObjectPoolProvider.md) | 类 | 对象池提供者（单例） |
| [GuidGenerator](./com.euonia.core.GuidGenerator.md) | 工具类 | .NET 兼容的 GUID 生成器 |
| [GuidType](./com.euonia.core.GuidType.md) | 枚举 | GUID 生成策略类型 |
| [ObjectId](./com.euonia.core.ObjectId.md) | 类 | 统一对象 ID（支持多种算法） |
| [ObjectPool](./com.euonia.core.ObjectPool.md) | 接口 | 对象池接口定义 |
| [ObjectPoolPolicy](./com.euonia.core.ObjectPoolPolicy.md) | 接口 | 对象池策略接口 |
| [ObjectPoolProvider](./com.euonia.core.ObjectPoolProvider.md) | 接口 | 对象池提供者接口 |
| [Pair](./com.euonia.core.Pair.md) | 记录类 | 键值对 |
| [PriorityQueue](./com.euonia.core.PriorityQueue.md) | 类 | 泛型优先级队列 |
| [PriorityValueFinder](./com.euonia.core.PriorityValueFinder.md) | 工具类 | 优先级队列值查找器 |
| [RandomId](./com.euonia.core.RandomId.md) | 工具类 | 随机 ID 生成器 |
| [ShortUniqueId](./com.euonia.core.ShortUniqueId.md) | 类 | 短唯一 ID 编码/解码 |
| [Singleton](./com.euonia.core.Singleton.md) | 工厂类 | 线程安全单例工厂 |
| [SnowflakeId](./com.euonia.core.SnowflakeId.md) | 类 | Snowflake 分布式 ID 生成器 |
| [ULID](./com.euonia.core.ULID.md) | 工具类 | ULID 生成器 |

### com.euonia.http

HTTP 异常层次结构与请求上下文抽象。

| 类 | 类型 | 说明 |
|----|------|------|
| [HttpStatusException](./com.euonia.http.HttpStatusException.md) | 抽象类 | HTTP 状态异常基类 |
| [BadRequestException](./com.euonia.http.BadRequestException.md) | 异常类 | 400 Bad Request |
| [ForbiddenException](./com.euonia.http.ForbiddenException.md) | 异常类 | 403 Forbidden |
| [ResourceNotFoundException](./com.euonia.http.ResourceNotFoundException.md) | 异常类 | 404 Not Found |
| [MethodNotAllowedException](./com.euonia.http.MethodNotAllowedException.md) | 异常类 | 405 Method Not Allowed |
| [ConflictException](./com.euonia.http.ConflictException.md) | 异常类 | 409 Conflict |
| [UpgradeRequiredException](./com.euonia.http.UpgradeRequiredException.md) | 异常类 | 426 Upgrade Required |
| [TooManyRequestsException](./com.euonia.http.TooManyRequestsException.md) | 异常类 | 429 Too Many Requests |
| [RequestTimeoutException](./com.euonia.http.RequestTimeoutException.md) | 异常类 | 408 Request Timeout |
| [InternalServerErrorException](./com.euonia.http.InternalServerErrorException.md) | 异常类 | 500 Internal Server Error |
| [BadGatewayException](./com.euonia.http.BadGatewayException.md) | 异常类 | 502 Bad Gateway |
| [ServiceUnavailableException](./com.euonia.http.ServiceUnavailableException.md) | 异常类 | 503 Service Unavailable |
| [GatewayTimeoutException](./com.euonia.http.GatewayTimeoutException.md) | 异常类 | 504 Gateway Timeout |
| [RequestContext](./com.euonia.http.RequestContext.md) | 接口 | 请求上下文 |
| [RequestContextAccessor](./com.euonia.http.RequestContextAccessor.md) | 接口 | 请求上下文访问器 |
| [DefaultRequestContextAccessor](./com.euonia.http.DefaultRequestContextAccessor.md) | 类 | 默认请求上下文访问器 |
| [DelegateRequestContextAccessor](./com.euonia.http.DelegateRequestContextAccessor.md) | 类 | 委托式请求上下文访问器 |
| [RequestContextAwareExecutor](./com.euonia.http.RequestContextAwareExecutor.md) | 类 | 请求上下文感知执行器 |
| [RequestContextCopyingDecorator](./com.euonia.http.RequestContextCopyingDecorator.md) | 类 | 请求上下文复制装饰器 |
| [ResponseHttpStatusCode](./com.euonia.http.ResponseHttpStatusCode.md) | 接口 | HTTP 状态码接口 |

### com.euonia.reflection

反射工具类和服务提供者抽象。

| 类 | 类型 | 说明 |
|----|------|------|
| [ClassScanner](./com.euonia.reflection.ClassScanner.md) | 类 | 类路径扫描器 |
| [ServiceProvider](./com.euonia.reflection.ServiceProvider.md) | 接口 | 服务提供者接口 |
| [SimpleServiceProvider](./com.euonia.reflection.SimpleServiceProvider.md) | 类 | 简单服务提供者实现 |
| [DelegateServiceProvider](./com.euonia.reflection.DelegateServiceProvider.md) | 类 | 委托式服务提供者 |
| [GenericType](./com.euonia.reflection.GenericType.md) | 抽象类 | 泛型类型捕获 |
| [SyntheticParameterizedType](./com.euonia.reflection.SyntheticParameterizedType.md) | 类 | 合成参数化类型 |
| [TypeHelper](./com.euonia.reflection.TypeHelper.md) | 工具类 | 类型转换助手 |
| [DisplayName](./com.euonia.reflection.DisplayName.md) | 注解 | 显示名称注解 |

### com.euonia.security

安全基础设施：认证异常和用户主体。

| 类 | 类型 | 说明 |
|----|------|------|
| [AccountException](./com.euonia.security.AccountException.md) | 异常类 | 账户异常 |
| [AuthenticationException](./com.euonia.security.AuthenticationException.md) | 异常类 | 认证异常 |
| [CredentialException](./com.euonia.security.CredentialException.md) | 异常类 | 凭证异常 |
| [UnauthorizedAccessException](./com.euonia.security.UnauthorizedAccessException.md) | 异常类 | 未授权访问异常 |
| [UserClaimTypes](./com.euonia.security.UserClaimTypes.md) | 常量类 | 用户声明类型常量 |
| [UserPrincipal](./com.euonia.security.UserPrincipal.md) | 接口 | 用户主体接口 |

### com.euonia.tuple

元组类型系列，从 1 元素到 10 元素。

| 类 | 元素数 | 说明 |
|----|--------|------|
| [Tuple](./com.euonia.tuple.Tuple.md) | 基类 | 元组基类 |
| [Solo](./com.euonia.tuple.Solo.md) | 1 | 单元素元组 |
| [Duet](./com.euonia.tuple.Duet.md) | 2 | 双元素元组 |
| [Trio](./com.euonia.tuple.Trio.md) | 3 | 三元素元组 |
| [Quartet](./com.euonia.tuple.Quartet.md) | 4 | 四元素元组 |
| [Quintet](./com.euonia.tuple.Quintet.md) | 5 | 五元素元组 |
| [Sextet](./com.euonia.tuple.Sextet.md) | 6 | 六元素元组 |
| [Septet](./com.euonia.tuple.Septet.md) | 7 | 七元素元组 |
| [Octet](./com.euonia.tuple.Octet.md) | 8 | 八元素元组 |
| [Nonet](./com.euonia.tuple.Nonet.md) | 9 | 九元素元组 |
| [Decet](./com.euonia.tuple.Decet.md) | 10 | 十元素元组 |

### com.euonia.utility

通用工具类。

| 类 | 类型 | 说明 |
|----|------|------|
| [Assert](./com.euonia.utility.Assert.md) | 工具类 | 断言工具 |
| [ObjectUtility](./com.euonia.utility.ObjectUtility.md) | 抽象工具类 | 对象反射操作工具 |
| [StringUtility](./com.euonia.utility.StringUtility.md) | 工具类 | 字符串操作工具 |

## 依赖

- `org.junit.jupiter:junit-jupiter` (test)

## 作者

- damon (zhaorong@outlook.com)
