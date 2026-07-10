# Euonia OSBA 模块 API 文档

## 概述

OSBA（Object System for Business Applications）模块是 Euonia 框架的核心业务对象系统，提供属性管理、规则检查、授权和属性变更通知等核心功能。该模块定义了业务对象的完整生命周期管理，包括创建、读取、更新、删除操作，以及基于注解的工厂模式。

- **Maven 坐标**: `com.euonia:osba`
- **Java 模块名**: `com.euonia.osba`

## 导出包

### com.euonia.osba

核心业务对象包，包含业务对象基类和可观察/可编辑对象的抽象实现。

| 类名 | 类型 | 说明 |
|------|------|------|
| [BusinessObject](./com.euonia.osba.BusinessObject.md) | abstract class | 业务对象的抽象基类，提供属性管理、规则检查、授权和属性变更通知 |
| [BusinessContext](./com.euonia.osba.BusinessContext.md) | class | 业务上下文，为工厂创建的业务对象提供服务解析和实例创建网关 |
| [EditableObject](./com.euonia.osba.EditableObject.md) | abstract class | 可编辑的业务对象，可保存到数据库或其他持久化存储 |
| [ExecutableObject](./com.euonia.osba.ExecutableObject.md) | abstract class | 可执行的业务对象 |
| [ObservableObject](./com.euonia.osba.ObservableObject.md) | abstract class | 可观察的业务对象，跟踪编辑状态和忙碌状态 |
| [ObservableList](./com.euonia.osba.ObservableList.md) | class | 可观察列表，提供子属性通知、集合变更通知和忙碌状态通知 |
| [ReadOnlyObject](./com.euonia.osba.ReadOnlyObject.md) | abstract class | 只读业务对象 |
| [ObjectChangedEventArgs](./com.euonia.osba.ObjectChangedEventArgs.md) | class | 属性更改或集合更改事件参数 |
| [ObjectEditState](./com.euonia.osba.ObjectEditState.md) | enum | 对象的编辑状态（NONE, NEW, CHANGED, DELETED） |
| [SavedEventArgs](./com.euonia.osba.SavedEventArgs.md) | class | 保存事件参数 |

### com.euonia.osba.abstracts

定义业务对象行为的抽象接口和契约。

| 类名 | 类型 | 说明 |
|------|------|------|
| [TrackableObject](./com.euonia.osba.abstracts.TrackableObject.md) | interface | 跟踪对象状态的接口（有效性、变更、删除、新建、可保存、忙碌） |
| [RuleCheckable](./com.euonia.osba.abstracts.RuleCheckable.md) | interface | 规则检查接口 |
| [Savable](./com.euonia.osba.abstracts.Savable.md) | interface | 可保存到持久化存储的标记接口 |
| [UseBusinessContext](./com.euonia.osba.abstracts.UseBusinessContext.md) | interface | 使用业务上下文的标记接口 |
| [OperableProperty](./com.euonia.osba.abstracts.OperableProperty.md) | interface | 可操作属性的契约接口 |

### com.euonia.osba.rules

规则引擎包，提供业务对象验证规则的定义和执行。

| 类名 | 类型 | 说明 |
|------|------|------|
| [Rule](./com.euonia.osba.rules.Rule.md) | interface | 规则接口，定义规则的基本契约 |
| [RuleBase](./com.euonia.osba.rules.RuleBase.md) | abstract class | 规则的基础实现 |
| [Rules](./com.euonia.osba.rules.Rules.md) | class | 规则管理器，管理验证规则执行 |
| [RuleManager](./com.euonia.osba.rules.RuleManager.md) | class | 按类型管理规则的线程安全容器 |
| [RuleContext](./com.euonia.osba.rules.RuleContext.md) | class | 规则执行上下文 |
| [RuleResult](./com.euonia.osba.rules.RuleResult.md) | class | 规则执行结果 |
| [RuleSeverity](./com.euonia.osba.rules.RuleSeverity.md) | enum | 规则严重级别（ERROR, WARNING, INFORMATION, SUCCESS） |
| [BrokenRule](./com.euonia.osba.rules.BrokenRule.md) | record | 已破坏的规则 |
| [BrokenRuleCollection](./com.euonia.osba.rules.BrokenRuleCollection.md) | class | 已破坏规则集合 |
| [RuleCheckException](./com.euonia.osba.rules.RuleCheckException.md) | class | 规则校验异常 |
| [LambdaRule](./com.euonia.osba.rules.LambdaRule.md) | class | Lambda 表达式验证规则 |
| [RequiredRule](./com.euonia.osba.rules.RequiredRule.md) | class | 必填验证规则 |
| [RegularRule](./com.euonia.osba.rules.RegularRule.md) | class | 正则表达式验证规则 |
| [DataAnnotationRule](./com.euonia.osba.rules.DataAnnotationRule.md) | class | 基于数据注解的验证规则 |

### com.euonia.factory

工厂模式包，定义业务对象创建和生命周期管理的工厂接口与实现。

| 类名 | 类型 | 说明 |
|------|------|------|
| [ObjectFactory](./com.euonia.factory.ObjectFactory.md) | interface | 对象工厂接口 |
| [BusinessObjectFactory](./com.euonia.factory.BusinessObjectFactory.md) | class | 基于反射的工厂实现 |

### com.euonia.factory.annotation

工厂方法注解，用于标记业务对象的工厂方法。

| 类名 | 类型 | 说明 |
|------|------|------|
| [FactoryCreate](./com.euonia.factory.annotation.FactoryCreate.md) | annotation | 标记创建对象的工厂方法 |
| [FactoryFetch](./com.euonia.factory.annotation.FactoryFetch.md) | annotation | 标记获取对象的工厂方法 |
| [FactoryInsert](./com.euonia.factory.annotation.FactoryInsert.md) | annotation | 标记插入对象的工厂方法 |
| [FactoryUpdate](./com.euonia.factory.annotation.FactoryUpdate.md) | annotation | 标记更新对象的工厂方法 |
| [FactoryDelete](./com.euonia.factory.annotation.FactoryDelete.md) | annotation | 标记删除对象的工厂方法 |
| [FactoryExecute](./com.euonia.factory.annotation.FactoryExecute.md) | annotation | 标记执行操作的工厂方法 |

### com.euonia.reflection

反射工具包，提供属性信息管理、方法查找和字段数据管理。

| 类名 | 类型 | 说明 |
|------|------|------|
| [PropertyInfo](./com.euonia.reflection.PropertyInfo.md) | class | 属性元数据信息 |
| [PropertyInfoList](./com.euonia.reflection.PropertyInfoList.md) | class | 线程安全的属性信息列表 |
| [PropertyInfoManager](./com.euonia.reflection.PropertyInfoManager.md) | class | 属性信息缓存管理器 |
| [FieldData](./com.euonia.reflection.FieldData.md) | class | 字段数据，跟踪字段变化 |
| [FieldDataManager](./com.euonia.reflection.FieldDataManager.md) | class | 字段数据管理器 |
| [ObjectReflector](./com.euonia.reflection.ObjectReflector.md) | class | 反射工具类 |
| [AmbiguousMethodException](./com.euonia.reflection.AmbiguousMethodException.md) | class | 方法歧义异常 |
| [MissingMethodException](./com.euonia.reflection.MissingMethodException.md) | class | 方法未找到异常 |

## 依赖

- `com.euonia:core` — 核心工具类（PriorityValueFinder 等）
- `com.euonia.security` — 安全相关（UnauthorizedAccessException）
- `com.euonia.annotation` — 注解定义（Validator, Validation, DisplayName）
- `com.euonia.http` — HTTP 相关（ResponseHttpStatusCode, RequestContextAwareExecutor）
- `com.euonia.tuple` — 元组类型（Duet）
- `com.euonia.utility` — 工具类（Assert）
