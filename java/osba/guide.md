# OSBA 模块 — 开发者手册

> 面向对象的可扩展业务架构（Object-Oriented Scalable Business Architecture）—— Euonia 的核心业务对象框架。提供丰富的业务对象层次结构，内置基于规则的验证、属性变更追踪、对象生命周期管理和注解驱动的工厂模式。

- **Maven 坐标**: `com.euonia:osba`
- **依赖**: `com.euonia:core`
- **API文档**：[点击查看](./apis)

---

## 架构

```text
                    ┌──────────────────────────┐
                    │     BusinessObject<B>      │
                    │  ┌──────────────────────┐ │
                    │  │ 规则管理               │ │  ← DataAnnotationRule、LambdaRule
                    │  │ BusinessContext        │ │  ← 服务解析
                    │  │ PropertyChangeSupport  │ │  ← 观察者模式
                    │  │ FieldDataManager       │ │  ← 基于反射的字段管理
                    │  └──────────────────────┘ │
                    └───────────┬──────────────┘
                                │
          ┌─────────────────────┼─────────────────────┐
          │                     │                     │
          ▼                     ▼                     ▼
┌─────────────────┐   ┌─────────────────┐   ┌─────────────────┐
│ ReadOnlyObject   │   │ObservableObject  │   │ ExecutableObject │
│  （不可变对象）    │   │  （状态追踪）     │   │  （操作型对象）   │
└─────────────────┘   └────────┬────────┘   └─────────────────┘
                               │
                               ▼
                      ┌─────────────────┐
                      │  EditableObject  │
                      │   （可保存对象）   │
                      └─────────────────┘

        BusinessObjectFactory
                │
                ├── @FactoryCreate   → 创建新实例
                ├── @FactoryFetch    → 从持久层检索
                ├── @FactoryInsert   → 持久化新增
                ├── @FactoryUpdate   → 持久化变更
                ├── @FactoryDelete   → 从持久层删除
                └── @FactoryExecute  → 执行操作
```

OSBA 围绕五个核心抽象构建：**业务对象层次结构**、**规则系统**、**工厂模式**、**反射系统** 和 **关键接口**。这些抽象共同工作，提供丰富的、具有内置规则、状态追踪和持久化能力的面向对象可扩展业务架构。

---

## 核心概念

### 业务对象层次结构

| 类 | 类型 | 描述 |
|----|------|------|
| `BusinessObject<B>` | `abstract class` | 核心基类 — 规则管理、`BusinessContext` 集成、属性变更支持、权限检查、基于反射的字段数据管理 |
| `ObservableObject<T>` | `abstract class` | 追踪编辑状态（`NONE`、`NEW`、`CHANGED`、`DELETED`）、忙碌计数器，并通过 `Flow.Publisher` 暴露异步观察能力 |
| `EditableObject<T>` | `abstract class` | 扩展 `ObservableObject`，实现 `Savable` 接口 — 异步规则校验保存、保存事件、删除追踪 |
| `ReadOnlyObject<T>` | `abstract class` | 面向不可变对象 — 禁用写访问并绕过默认规则 |
| `ExecutableObject<T>` | `abstract class` | 面向操作型对象 — 提供 `execute()` 和 `create()` 方法 |

### 规则系统

| 类 / 接口 | 类型 | 描述 |
|-----------|------|------|
| `Rule` | `interface` | 带优先级的验证规则接口 |
| `RuleBase` | `abstract class` | 自定义规则的抽象基类 |
| `RuleManager` | `class` | 每个类型的单例规则注册表（`ConcurrentHashMap`） |
| `Rules` | `class` | 实例级异步规则执行器，基于 `CompletableFuture` |
| `LambdaRule` | `class` | 基于 Lambda 表达式的规则执行 |
| `DataAnnotationRule` | `class` | 注解驱动的规则 — `@Required`、`@Validator` |
| `BrokenRule` | `class` | 规则违规，包含 `property`、`severity`、`description` |
| `BrokenRuleCollection` | `class` | 追踪错误、警告和信息级别的违规 |
| `RuleContext` | `class` | 验证期间传递给规则的执行上下文 |
| `RuleResult` | `class` | 规则执行结果 |
| `RuleSeverity` | `enum` | 规则严重程度（Error、Warning、Information） |
| `RuleCheckException` | `class` | 规则检查异常 |

### 工厂模式

| 注解 | 生命周期方法 |
|------|-------------|
| `@FactoryCreate` | 创建新对象实例 |
| `@FactoryFetch` | 按 ID 从持久层检索 |
| `@FactoryInsert` | 持久化新对象 |
| `@FactoryUpdate` | 持久化对象变更 |
| `@FactoryDelete` | 从持久层删除 |
| `@FactoryExecute` | 执行自定义操作 |

`BusinessObjectFactory` 通过反射在运行时发现带注解的工厂方法，`ObjectFactory` 提供 `create()` 和 `execute()` 快捷方法。

### 反射系统

| 类 | 类型 | 描述 |
|----|------|------|
| `PropertyInfo<T>` | `class` | 类型化属性元数据 — 名称、类型、友好名称、默认值 |
| `FieldData<T>` | `class` | 实例属性值存储，包含变更追踪和 Publisher 支持 |
| `FieldDataManager` | `class` | 管理单个对象实例的所有字段数据 |
| `PropertyInfoManager` | `class` | 给定类型的 `PropertyInfo` 注册表 |
| `ObjectReflector` | `final class` | 带缓存的工厂方法查找静态工具类 |

### 关键接口

| 接口 | 描述 |
|------|------|
| `RuleCheckable` | `isValid()`、`getBrokenRules()`、`ruleCheckComplete()` |
| `TrackableObject` | `isValid()`、`isChanged()`、`isDeleted()`、`isNew()`、`isSavable()`、`isBusy()` |
| `Savable<T>` | `save(forceUpdate)`、`saveComplete()` |
| `OperableProperty` | 带类型化 `PropertyInfo` 的 `getProperty()`、`setProperty()` |
| `UseBusinessContext` | `setBusinessContext()`、`getBusinessContext()` |

### BusinessContext

- 为业务对象提供服务解析能力
- 通过 `Function<Class<?>, ?>` 管理实例创建
- 通常从 Spring `ApplicationContext` 或自定义 DI 容器注入
- 与 `BusinessObjectFactory` 集成

---

## 设计模式

| 模式 | 使用场景 |
|------|---------|
| **工厂模式** | `BusinessObjectFactory` 基于反射的注解方法查找 |
| **观察者模式** | `PropertyChangeSupport`、`Flow.Publisher` 实现响应式属性变更 |
| **模板方法** | 抽象生命周期钩子：`addRules()`、`initialize()`、`onBusinessContextSet()` |
| **单例模式** | 按类型的 `RuleManager`、按对象的字段数据管理器 |
| **策略模式** | 可插拔的规则类型 — `LambdaRule`、`DataAnnotationRule`、自定义 `RuleBase` |

---

## 快速入门

### 第一步：添加依赖

```xml
<dependency>
    <groupId>com.euonia</groupId>
    <artifactId>osba</artifactId>
    <version>1.0.0</version>
</dependency>
```

### 第二步：定义业务对象

```java
public class User extends EditableObjectBase<User, Long> {

    private final PropertyInfo<Long> id = registerProperty(Long.class, "id");

    @DisplayName("User Name")
    @Required(message = "name is valid")
    private final PropertyInfo<String> name = registerProperty(String.class, "name");

    @DisplayName("User age")
    private final PropertyInfo<Integer> age = registerProperty(Integer.class, "age");

    public Long getId() { return getProperty(id); }
    public void setId(Long id) { loadProperty(this.id, id); }

    public String getName() { return getProperty(this.name); }
    public void setName(String name) { setProperty(this.name, name); }

    public int getAge() { return getProperty(age); }
    public void setAge(int age) { setProperty(this.age, age); }

    @Override
    protected void addRules() {
        super.addRules();
        getRules().addRule(new UserNameRule(this.name));
        getRules().addRule(new LambdaRule<>(this.age,
            (age, context) -> age != null && age >= 18,
            "Age must be at least 18"));
    }

    @FactoryCreate
    protected void create(String name) {
        super.create();
        setName(name);
        setId(Objects.requireNonNull(ObjectId.snowflake().getValue(Long.class)));
        raiseEvent(new UserCreatedEvent(getId(), name));
    }
}
```

### 第三步：定义自定义规则

```java
// 继承 RuleBase 定义嵌套的自定义规则
public class UserNameRule extends RuleBase {
    public UserNameRule(PropertyInfo<?> property) { super(property); }

    @Override
    public CompletableFuture<Void> executeAsync(RuleContext context) {
        return CompletableFuture.runAsync(() -> {
            if (!(context.getTarget() instanceof User user)) return;
            var name = user.getName();
            if (name == null || name.trim().isEmpty()) {
                context.addErrorResult(
                    String.format("%s 不能为空", getProperty().getFriendlyName()));
            } else if (name.length() < 12) {
                context.addErrorResult(
                    String.format("%s 必须为 12 个字符", getProperty().getFriendlyName()));
            }
        });
    }
}
```

### 第四步：通过工厂创建和使用

```java
// 创建工厂
BusinessObjectFactory factory = new BusinessObjectFactory(serviceProvider);

// 创建新的 User 实例
User user = factory.create(User.class, "张三");

// 验证
boolean isValid = user.isValid();
if (!isValid) {
    BrokenRuleCollection brokenRules = user.getBrokenRules();
    // 处理验证错误
}

// 保存（异步）
user.save(false).thenRun(() -> {
    System.out.println("User saved: " + user.getId());
});
```

---

## 使用示例

### Lambda 规则

快速定义内联验证规则：

```java
getRules().addRule(new LambdaRule<>(this.age,
    (age, context) -> {
        if (age == null || age < 18) {
            context.addErrorResult("年龄必须至少为 18 岁");
        }
        if (age != null && age > 150) {
            context.addErrorResult("年龄不能超过 150 岁");
        }
    })
);
```

### 注解驱动的验证规则

使用 `DataAnnotationRule` 自动应用 `@Required`、`@Range`、`@StringLength` 等注解约束：

```java
@DisplayName("邮箱")
@Required(message = "邮箱不能为空")
@RegularExpression(value = "^[\\w.-]+@[\\w.-]+\\.[a-z]{2,}$", message = "邮箱格式不正确")
private final PropertyInfo<String> email = registerProperty(String.class, "email");

// addRules() 中添加 DataAnnotationRule 即可自动应用所有注解约束
@Override
protected void addRules() {
    super.addRules();
    getRules().addRule(new DataAnnotationRule(this.email));
}
```

### 属性变更观察

通过 `PropertyChangeSupport` 监听属性变更：

```java
user.addPropertyChangeListener(evt -> {
    System.out.println("属性变更: " + evt.getPropertyName()
        + " = " + evt.getOldValue() + " → " + evt.getNewValue());
});

user.setName("新用户名");
// 输出: 属性变更: name = 张三 → 新用户名
```

### 状态追踪

`ObservableObject` 提供编辑状态追踪：

```java
ObservableObject<User> user = new User();
// user.getEditState() == ObjectEditState.NONE

user.setName("张三");
// user.getEditState() == ObjectEditState.NEW（如果是新对象）或 ObjectEditState.CHANGED

user.markAsUnchanged();
// 清除变更历史

// 检查对象状态
boolean changed = user.isChanged();   // 是否有未保存的变更
boolean valid = user.isValid();       // 是否通过所有规则验证
boolean busy = user.isBusy();         // 是否有挂起的异步操作
```

### @PipelineBehaviors 上下文类

工厂方法通过 `@FactoryCreate` 等注解标记，在运行时由 `ObjectReflector` 基于反射发现：

```java
@FactoryCreate
protected void create(String name) {
    super.create();
    setName(name);
    // 初始化默认值、生成 ID、发布事件等
}

@FactoryFetch
protected void fetch(Long id) {
    // 从持久层加载数据
    loadProperty(this.id, id);
    // loadProperty 会将字段标记为"未变更"，避免假变更检测
}

@FactoryUpdate
protected void update(String name, int age) {
    setProperty(this.name, name);  // 追踪变更
    setProperty(this.age, age);
}

@FactoryDelete
protected void delete() {
    // 标记为已删除
    markDeleted();
}
```

### 使用 ObjectFactory 快捷方法

```java
ObjectFactory objectFactory = new ObjectFactory(factory);

// 创建并保存
User user = objectFactory.create(User.class, "张三");
objectFactory.insert(user);

// 获取
User existing = objectFactory.fetch(User.class, 123L);

// 更新
existing.setName("新名称");
objectFactory.update(existing);

// 删除
objectFactory.delete(existing);
```

---

## API 参考

### BusinessObject\<B\>

> `abstract class` `implements UseBusinessContext, RuleCheckable, AutoCloseable` — 业务对象的抽象基类，提供属性管理、规则检查、授权和属性变更通知等核心功能。

| 字段 | 类型 | 描述 |
|------|------|------|
| `support` | `PropertyChangeSupport` | 属性变更支持对象，用于触发属性变更事件 |

#### setBusinessContext(BusinessContext businessContext)

设置业务上下文。

- **Parameters**:
  - `businessContext` (`BusinessContext`): 业务上下文

#### getBusinessContext() → BusinessContext

获取业务上下文。

#### onBusinessContextSet()

当业务上下文设置完成后调用的生命周期钩子。

#### initialize()

初始化业务对象。

#### getFieldManager() → FieldDataManager

获取字段数据管理器的实例。使用双重检查锁定确保线程安全初始化。

#### getRules() → Rules

获取规则管理器的实例。使用双重检查锁定确保线程安全初始化。

#### addRules()

子类重写此方法以添加自定义规则。

#### isValid() → boolean

检查业务对象是否通过所有规则验证。

#### getBrokenRules() → BrokenRuleCollection

获取所有未通过验证的规则。

#### ruleCheckComplete()

规则检查完成后的回调。

---

### ObservableObject\<T\>

> `abstract class` — 可观察的业务对象，追踪编辑状态和忙碌状态。实现了 `TrackableObject` 接口，并通过 `SubmissionPublisher` 提供异步通知。

| 字段 | 类型 | 描述 |
|------|------|------|
| `editState` | `ObjectEditState` | 当前对象的编辑状态（NONE, NEW, CHANGED, DELETED） |

#### getEditState() → ObjectEditState

获取当前编辑状态。

#### setEditState(ObjectEditState state)

设置编辑状态。

#### isBusy() → boolean

检查对象是否处于忙碌状态（有挂起的异步操作）。

#### beginBusy()

增加忙碌计数器，进入忙碌状态。

#### endBusy()

减少忙碌计数器，可能的退出忙碌状态。

#### subscribe(Subscriber\<ObjectChangedEventArgs\> subscriber)

订阅对象变更通知。

---

### EditableObject\<T\>

> `abstract class` `implements Savable<T>` — 可编辑的业务对象，可保存到数据库或其他持久化存储。扩展 `ObservableObject`，在保存前自动进行规则检查。

#### save(boolean forceUpdate) → CompletableFuture\<T\>

异步保存对象。在持久化之前进行规则检查，验证失败则返回包含异常的 Future。

- **Parameters**:
  - `forceUpdate` (`boolean`): 若为 true 则忽略变更检查强制保存
- **Returns**: `CompletableFuture<T>` — 保存完成后的对象

#### saveComplete(T result)

保存完成后的回调钩子。

#### delete() → CompletableFuture\<T\>

异步删除当前对象。

#### markDeleted()

将对象标记为已删除。

---

### ReadOnlyObject\<T\>

> `abstract class` — 只读业务对象。禁用写访问并绕过默认规则，适用于不可变数据对象。

---

### ExecutableObject\<T\>

> `abstract class` — 可执行的业务对象。提供 `execute()` 和 `create()` 方法，适用于操作型对象。

#### execute() → CompletableFuture\<T\>

执行当前对象所代表的操作。

#### create() → CompletableFuture\<T\>

创建并初始化一个新的可执行对象实例。

---

### Rule 系统

#### Rule (interface)

验证规则接口，带优先级排序。

| 方法 | 描述 |
|------|------|
| `executeAsync(RuleContext) → CompletableFuture<Void>` | 异步执行规则的验证逻辑 |
| `getPriority() → int` | 获取规则优先级（数值越小优先级越高） |
| `getProperty() → PropertyInfo<?>` | 获取此规则关联的属性 |

#### RuleBase

> `abstract class` — 规则的抽象基类，提供属性和优先级的基本实现。

- **Fields**: `property` (PropertyInfo<?>), `priority` (int)
- **Constructors**: `RuleBase(PropertyInfo<?>)`, `RuleBase(PropertyInfo<?>, int)`

#### Rules

> `class` — 管理 `RuleManager` 实例的规则执行器。提供异步执行和管理规则列表的方法，所有规则操作均基于 `CompletableFuture` 实现非阻塞处理。

| 方法 | 描述 |
|------|------|
| `addRule(Rule)` | 添加一个规则到当前集合 |
| `checkRulesAsync() → CompletableFuture<Boolean>` | 异步执行所有规则，返回验证是否全部通过 |
| `getBrokenRules() → BrokenRuleCollection` | 获取所有已损坏的规则 |
| `clearRules()` | 清除所有规则 |

#### RuleManager

> `class` — 管理与特定类型关联的规则。线程安全，使用 `ConcurrentMap` 和 `CopyOnWriteArrayList`。

| 方法 | 描述 |
|------|------|
| `getRules(type) → RuleManager` | 获取或创建指定类型的 RuleManager |
| `getRules() → List<Rule>` | 获取当前类型的规则列表 |
| `cleanRules(type)` | 移除指定类型的所有规则 |
| `isInitialized() → boolean` | 判断规则管理器是否已完成初始化 |
| `setInitialized(boolean)` | 设置初始化状态 |

#### LambdaRule

> `class` — 基于 Lambda 表达式的规则，快速定义内联验证逻辑。

- **Constructor**: `LambdaRule(PropertyInfo<T>, BiConsumer<T, RuleContext>)` — 不带 message
- **Constructor**: `LambdaRule(PropertyInfo<T>, BiConsumer<T, RuleContext>, String)` — 带自定义 message

#### DataAnnotationRule

> `class` `extends RuleBase` — 注解驱动的规则，用于处理 `@Required`、`@Range`、`@StringLength`、`@RegularExpression` 等约束注解。

#### BrokenRule

> `class` — 表示一个已损坏的规则，包含违规详情。

| 字段 | 类型 | 描述 |
|------|------|------|
| `property` | `String` | 违规的属性名 |
| `severity` | `RuleSeverity` | 严重程度 |
| `description` | `String` | 违规描述 |

#### BrokenRuleCollection

> `class` `extends ArrayList<BrokenRule>` — 跟踪和分类错误、警告和信息级别的违规。

| 方法 | 描述 |
|------|------|
| `getErrors() → List<BrokenRule>` | 获取所有 Error 级别的违规 |
| `getWarnings() → List<BrokenRule>` | 获取所有 Warning 级别的违规 |
| `getInfos() → List<BrokenRule>` | 获取所有 Information 级别的违规 |
| `hasErrors() → boolean` | 是否有 Error 级别违规 |
| `addError(String, String)` | 添加一个 Error 级别违规 |

#### RuleContext

> `class` — 规则执行上下文，在验证期间传递给规则。

| 方法 | 描述 |
|------|------|
| `getTarget() → Object` | 获取被验证的目标对象 |
| `addErrorResult(String)` | 添加一个 Error 级别结果 |
| `addWarningResult(String)` | 添加一个 Warning 级别结果 |
| `addInfoResult(String)` | 添加一个 Information 级别结果 |
| `getBrokenRules() → BrokenRuleCollection` | 获取所有已收集的违规 |

#### RuleSeverity

> `enum` — 规则严重程度枚举。

| 值 | 描述 |
|----|------|
| `Error` | 错误级别，阻止保存 |
| `Warning` | 警告级别，不阻止但需关注 |
| `Information` | 信息级别，仅供记录 |

---

### 工厂系统

#### BusinessObjectFactory

> `class` — 业务对象工厂，通过反射在运行时发现带注解的工厂方法，同时支持 Spring `ApplicationContext` 和自定义 Bean 工厂。

| 方法 | 描述 |
|------|------|
| `create(Class<T>, Object...) → T` | 创建新对象实例，调用 `@FactoryCreate` 方法 |
| `fetch(Class<T>, Object...) → T` | 从持久层检索，调用 `@FactoryFetch` 方法 |
| `insert(T) → T` | 持久化新对象，调用 `@FactoryInsert` 方法 |
| `update(T) → T` | 持久化变更，调用 `@FactoryUpdate` 方法 |
| `delete(T) → T` | 删除对象，调用 `@FactoryDelete` 方法 |
| `execute(Class<T>, Object...) → T` | 执行自定义操作，调用 `@FactoryExecute` 方法 |

#### ObjectFactory

> `class` — `BusinessObjectFactory` 的便捷包装，提供简化的创建和执行方法。

#### 工厂注解

| 注解 | 目标 | 描述 |
|------|------|------|
| `@FactoryCreate` | METHOD | 标记创建新对象的工厂方法 |
| `@FactoryFetch` | METHOD | 标记从持久层检索的工厂方法 |
| `@FactoryInsert` | METHOD | 标记持久化新对象的工厂方法 |
| `@FactoryUpdate` | METHOD | 标记持久化变更的工厂方法 |
| `@FactoryDelete` | METHOD | 标记删除对象的工厂方法 |
| `@FactoryExecute` | METHOD | 标记执行自定义操作的工厂方法 |

---

### 反射系统

#### PropertyInfo\<T\>

> `class` `implements Comparable<PropertyInfo<T>>` — 业务对象属性的元数据，包括名称、类型、默认值和显示名称。

| 方法 | 描述 |
|------|------|
| `getName() → String` | 获取属性名 |
| `getFriendlyName() → String` | 获取显示名称（优先使用 `@DisplayName` 值） |
| `getType() → Class<T>` | 获取属性类型 |
| `getDefaultValue() → T` | 获取默认值 |
| `isChild() → boolean` | 属性是否为子 `BusinessObject` |
| `getField() → Field` | 获取对应的反射 Field |

#### FieldData\<T\>

> `class` `implements TrackableObject` — 单个属性的值存储，包含变更追踪、历史记录和基于 `SubmissionPublisher` 的响应式通知。

| 方法 | 描述 |
|------|------|
| `getValue() → T` | 获取当前值 |
| `setValue(T)` | 设置新值并推送到 Subscriber |
| `markAsUnchanged()` | 将字段标记为未更改，清除历史记录 |
| `undo()` | 撤销最后一次更改 |

#### FieldDataManager

> `class` — 管理单个对象实例的所有字段数据，维护属性到值的映射并提供线程安全的访问。

| 方法 | 描述 |
|------|------|
| `getFieldData(PropertyInfo<T>) → FieldData<T>` | 获取属性对应的字段数据 |
| `getOrCreateFieldData(PropertyInfo<T>) → FieldData<T>` | 获取或创建字段数据 |
| `setFieldData(PropertyInfo<T>, T)` | 设置字段值 |
| `loadFieldData(PropertyInfo<T>, T)` | 加载字段值并标记为未更改 |
| `removeFieldData(PropertyInfo<?>)` | 移除字段数据 |
| `isBusy() → boolean` | 检查任何字段是否忙碌 |

#### PropertyInfoManager

> `class` — 管理给定类型的所有 `PropertyInfo` 注册表。使用 `ConcurrentHashMap` 缓存。

| 方法 | 描述 |
|------|------|
| `getPropertyListCache(Type) → PropertyInfoList` | 获取类型的属性列表缓存 |
| `getRegisteredProperties(Type) → PropertyInfoList` | 获取已注册的属性列表 |
| `registerProperty(Type, PropertyInfo<?>) → PropertyInfo<?>` | 注册新属性 |

#### ObjectReflector

> `final class` — 静态反射工具类，提供基于注解的工厂方法查找，带缓存支持。

| 方法 | 描述 |
|------|------|
| `findFactoryMethod(Class<T>, Class<A>, Object[]) → Method` | 根据目标类型、注解类型和参数查找匹配的工厂方法 |

---

## 依赖

- `com.euonia:core` (compile)
- `org.junit.jupiter:junit-jupiter` (test)

## 作者

damon (zhaorong@outlook.com)
