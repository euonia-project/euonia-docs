# Pipeline 模块 — 开发者手册

> 一个轻量级的异步中间件管道框架，受 ASP.NET Core 管道模式启发。提供统一的 `Pipeline<TRequest, TResponse>` 构建器，包含泛型行为（Behaviors）、委托（Delegates）和可插拔的依赖注入。

- **Maven 坐标**: `com.euonia:pipeline`
- **依赖**: `com.euonia:core`
- **API文档**：[点击查看](./apis)

---

## 架构

```text
  TRequest
        │
        ▼
┌──────────────────────┐
│  Pipeline.use(…)     │  ← 行为 1（日志、认证、验证…）
├──────────────────────┤
│  Pipeline.use(…)     │  ← 行为 2（转换、增强…）
├──────────────────────┤
│  Pipeline.use(…)     │  ← 行为 N
├──────────────────────┤
│  终端处理器           │  ← PipelineDelegate<TRequest, TResponse>
└──────────────────────┘
        │
        ▼
  TResponse
```

每个行为是一个**中间件**，接收请求和一个 `next` 委托。行为可以：

- 在下一个组件**之前**执行代码
- 在下一个组件**之后**执行代码（通过返回的 `CompletionStage`）
- **不调用** `next.invoke()` 来**短路**管道
- **转换**响应后再向上游返回

对于即发即忘的场景，使用 `Pipeline<Object, Void>` — 管道返回 `CompletionStage<Void>`。

---

## 核心概念

| 接口 / 类 | 类型 | 描述 |
|-----------|------|------|
| `Pipeline<TRequest, TResponse>` | `interface` | 构建器接口 — 通过 `.use()` 链式组合行为，然后调用 `.build()` 或 `.runAsync()` |
| `PipelineBase<TRequest, TResponse>` | `abstract class` | 抽象实现，包含组件列表、反向链构建和 `@PipelineBehaviors` 支持 |
| `PipelineDelegate<TRequest, TResponse>` | `@FunctionalInterface` | `CompletionStage<TResponse> invoke(TRequest request)` |
| `PipelineBehavior<TRequest, TResponse>` | `interface` | 行为契约 — `handleAsync(TRequest context, PipelineDelegate next)` |
| `PipelineFactory` | `interface` | 创建 `Pipeline` 实例 |
| `DefaultPipelineFactory` | `class` | 基于 `ServiceProvider` 的默认工厂 |
| `DefaultPipelineProvider` | `class` | 默认 `Pipeline` 实现，支持基于反射的行为解析 |
| `@PipelineBehaviors` | `annotation` | 从上下文类型自动发现行为的注解 |

---

## 快速入门

### 第一步：添加依赖

```xml
<dependency>
    <groupId>com.euonia</groupId>
    <artifactId>pipeline</artifactId>
    <version>1.0.0</version>
</dependency>
```

### 第二步：即发即忘管道

```java
import com.euonia.pipeline.*;
import com.euonia.reflection.SimpleServiceProvider;

// 创建解析器和管道
var resolver = new SimpleServiceProvider();
Pipeline<Object, Void> pipeline = new DefaultPipelineProvider<>(resolver)
        .use((ctx, next) -> {
            System.out.println("Before: " + ctx);
            return next.invoke(ctx).thenRun(() -> System.out.println("After: " + ctx));
        });

// 运行
pipeline.runAsync("Hello, Pipeline!")
        .toCompletableFuture()
        .join();
```

### 第三步：自定义行为类

```java
public class LoggingBehavior<TRequest, TResponse> implements PipelineBehavior<TRequest, TResponse> {
    @Override
    public CompletionStage<TResponse> handleAsync(TRequest context, PipelineDelegate<TRequest, TResponse> next) {
        long start = System.nanoTime();
        return next.invoke(context).thenRun(() -> {
            long elapsed = (System.nanoTime() - start) / 1_000_000;
            System.out.println("[" + context.getClass().getSimpleName() + "] 耗时 " + elapsed + "ms");
        });
    }
}

// 使用
Pipeline<Object, Void> pipeline = new DefaultPipelineProvider<>(resolver)
    .use(LoggingBehavior.class)
    .use((ctx, next) -> next.invoke(ctx));
```

### 第四步：类型化请求/响应管道

```java
Pipeline<Integer, Integer> pipeline = new DefaultPipelineProvider<>(resolver);
pipeline.use(PlusOneBehavior.class);

int result = pipeline.runAsync(2, request -> CompletableFuture.completedFuture(request * 2))
    .toCompletableFuture()
    .join();
// result == 5  (2 * 2 + 1)
```

**PlusOneBehavior：**

```java
public class PlusOneBehavior implements PipelineBehavior<Integer, Integer> {
    @Override
    public CompletionStage<Integer> handleAsync(Integer context,
                                                 PipelineDelegate<Integer, Integer> next) {
        return next.invoke(context).thenApply(value -> value + 1);
    }
}
```

---

## 使用示例

### Lambda 行为

```java
// 内联 lambda（即发即忘）
Pipeline<Object, Void> pipeline = new DefaultPipelineProvider<>(resolver);
pipeline.use((ctx, next) -> {
    System.out.println("Processing: " + ctx);
    return next.invoke(ctx);
});

// 内联 lambda（类型化请求/响应）
Pipeline<String, String> typedPipeline = new DefaultPipelineProvider<>(resolver);
typedPipeline.use((String req, PipelineDelegate<String, String> next) ->
    next.invoke(req).thenApply(resp -> "Wrapped: " + resp)
);
```

### 通过 ServiceProvider 进行依赖注入

行为可以声明除上下文以外的额外参数 — 它们会从 `ServiceProvider` 自动解析。

```java
// 定义服务
public class SuffixService {
    private final String suffix;
    public SuffixService(String suffix) { this.suffix = suffix; }
    public String apply(String value) { return value + suffix; }
}

// 注册
resolver.register(SuffixService.class, new SuffixService("-ok"));

// 具有自动解析依赖的管道行为
public class ReflectionBehavior {
    private final PipelineDelegate<String, String> next;

    public ReflectionBehavior(PipelineDelegate<String, String> next) {
        this.next = next;
    }

    public CompletionStage<String> handleAsync(String context, SuffixService suffixService) {
        return next.invoke(context).thenApply(value -> suffixService.apply(value));
    }
}

// 使用
Pipeline<String, String> pipeline = new DefaultPipelineProvider<>(resolver);
pipeline.use(ReflectionBehavior.class);
String result = pipeline.runAsync("input", CompletableFuture::completedFuture)
    .toCompletableFuture()
    .join();
// result == "input-ok"
```

### @PipelineBehaviors — 自动发现

在上下文类上添加注解，自动附加相关的行为：

```java
@PipelineBehaviors({ValidationBehavior.class, AuditBehavior.class})
public class CreateOrderCommand {
    // ...
}

// 调用 runAsync 时，注解会被自动发现：
Pipeline<CreateOrderCommand, Void> pipeline = new DefaultPipelineProvider<>(resolver);
pipeline.runAsync(new CreateOrderCommand())
    .toCompletableFuture()
    .join();
// ValidationBehavior 和 AuditBehavior 会在所有手动注册的行为之前执行
```

### Fluent Builder 与复合管道

```java
Pipeline<Object, Void> pipeline = pipelineFactory.<Object, Void>create()
    .use(AuthenticationBehavior.class)
    .use(AuthorizationBehavior.class)
    .use(ValidationBehavior.class, 0)  // 插入到指定索引位置
    .use((ctx, next) -> next.invoke(ctx))
    .build();  // 冻结管道，清空组件列表
```

### 在 handle / handleAsync 中解析依赖参数

使用普通类（不实现 `PipelineBehavior`）编写的行为通过反射解析。第一个参数是**上下文**，后续参数从 `ServiceProvider` **自动注入**：

```java
// 普通类 — 方法名必须为 "handle" 或 "handleAsync"，返回类型必须为 CompletionStage
public class MyBehavior<TRequest, TResponse> {
    private final PipelineDelegate<TRequest, TResponse> next;

    public MyBehavior(PipelineDelegate<TRequest, TResponse> next) {
        this.next = next;
    }

    // 上下文 + 自动注入的服务
    public CompletionStage<TResponse> handleAsync(TRequest ctx, LoggerService logger, MetricsService metrics) {
        logger.info("Processing " + ctx);
        metrics.increment();
        return next.invoke(ctx);
    }
}
```

---

## Spring Boot 集成

### 配置

```java
@Configuration
public class PipelineConfiguration {

    @Bean
    public PipelineFactory pipelineFactory(ServiceProvider resolver) {
        return new DefaultPipelineFactory(resolver);
    }
}
```

### 在行为中使用 Spring 管理的 Bean

行为可以通过构造函数参数注入任何 Spring Bean。`ApplicationContextServiceProvider`（来自 `euonia-spring` 模块）会自动处理自动装配。

```java
@Component
public class SpringLoggingBehavior implements PipelineBehavior<Object, Void> {
    private final PipelineDelegate<Object, Void> next;
    private final LoggerService logger;  // Spring Bean

    public SpringLoggingBehavior(PipelineDelegate<Object, Void> next, LoggerService logger) {
        this.next = next;
        this.logger = logger;
    }

    @Override
    public CompletionStage<Void> handleAsync(Object ctx, PipelineDelegate<Object, Void> next) {
        logger.info("管道处理: " + ctx);
        return next.invoke(ctx);
    }
}
```

```java
@Autowired
private PipelineFactory pipelineFactory;

public void execute() {
    Pipeline<MyCommand, Void> pipeline = pipelineFactory.<MyCommand, Void>create()
        .use(SpringLoggingBehavior.class)
        .use(TransactionalBehavior.class);

    pipeline.runAsync(new MyCommand()).toCompletableFuture().join();
}
```

---

## API 参考

### Pipeline\<C, R\>

> `interface` — 管道接口，定义了构建和执行组件管道的契约。组件可以按特定顺序或根据其类型添加，管道可以使用可选的累积函数来执行。

| 方法 | 描述 |
|------|------|
| `use(component)` | 添加一个 `Function<PipelineDelegate, PipelineDelegate>` 组件 |
| `use(component, index)` | 在指定索引位置插入组件 |
| `use(handler)` | 添加一个 `BiFunction<C, PipelineDelegate, CompletionStage<R>>` 处理器 |
| `use(type, args)` | 从指定类解析并添加一个组件 |
| `useOf(contextType, useAheadOfOthers)` | 自动发现上下文类型上的 `@PipelineBehaviors` 注解 |
| `build() → PipelineDelegate` | 构建并返回最外层的委托 |
| `runAsync(request) → CompletionStage<R>` | 快捷方式：发现行为 + 构建 + 执行 |
| `runAsync(request, accumulate)` | 带有终端累积函数的快捷方式 |

#### use(Function\<PipelineDelegate, PipelineDelegate\> component)

向管道添加组件。

- **Parameters**:
  - `component` (`Function<PipelineDelegate<C,R>, PipelineDelegate<C,R>>`): 要添加到管道的组件
- **Returns**: `Pipeline<C, R>` — 当前管道实例（支持链式调用）

#### use(component, int index)

在指定索引位置向管道添加组件。

- **Parameters**:
  - `component` (`Function<PipelineDelegate<C,R>, PipelineDelegate<C,R>>`): 要添加的组件
  - `index` (`int`): 插入位置的索引
- **Returns**: `Pipeline<C, R>`

#### use(BiFunction\<C, PipelineDelegate, CompletionStage\<R\>\> handler)

向管道添加一个 Lambda 处理器。

- **Parameters**:
  - `handler` (`BiFunction<C, PipelineDelegate<C,R>, CompletionStage<R>>`): 要添加的处理器
- **Returns**: `Pipeline<C, R>`

#### use(Class\<?\> type, Object... args)

根据类型向管道添加组件，支持可选的构造函数参数。

- **Parameters**:
  - `type` (`Class<?>`): 组件的类类型
  - `args` (`Object...`): 组件构造函数的可选参数
- **Returns**: `Pipeline<C, R>`

#### useOf(Class\<?\> contextType, boolean useAheadOfOthers)

根据上下文类型向管道添加组件。如果 `contextType` 标注了 `@PipelineBehaviors`，则自动添加关联的行为组件。

- **Parameters**:
  - `contextType` (`Class<?>`): 组件的上下文类型
  - `useAheadOfOthers` (`boolean`): 是否将组件添加在其他组件之前
- **Returns**: `Pipeline<C, R>`

#### build()

构建管道。将组件列表反转后依次应用，形成完整的委托链。构建后组件列表被清空。

- **Returns**: `PipelineDelegate<C, R>` — 构建好的管道委托

#### runAsync(C request)

使用给定的请求异步运行管道。自动调用 `useOf` 发现请求类型的关联行为，然后构建并执行。

- **Parameters**:
  - `request` (`C`): 要通过管道传递的请求对象
- **Returns**: `CompletionStage<R>` — 异步执行结果

#### runAsync(C request, Function\<C, CompletionStage\<R\>\> accumulate)

使用给定的请求和累积函数异步运行管道。

- **Parameters**:
  - `request` (`C`): 请求对象
  - `accumulate` (`Function<C, CompletionStage<R>>`): 用于累积多个组件结果的函数
- **Returns**: `CompletionStage<R>`

---

### PipelineBase\<C, R\>

> `abstract class` `implements Pipeline<C, R>` — Pipeline 接口的抽象实现，提供了构建和执行组件管道的基本功能。

#### getComponents() → List\<...\>

获取管道中组件的只读列表。

#### getNext(PipelineDelegate next, Class\<?\> type, Object... args)

*abstract* — 获取下一个 PipelineDelegate 实例，基于指定的类型和构造函数参数创建组件实例。

- **Parameters**:
  - `next` (`PipelineDelegate<C, R>`): 下一个 PipelineDelegate 实例
  - `type` (`Class<?>`): 组件的类类型
  - `constructorArguments` (`Object...`): 组件构造函数的参数
- **Returns**: `PipelineDelegate<C, R>` — 包含新组件的委托

> **实现说明**：`build()` 方法将组件列表反转后依次应用：每个组件函数接收"内部"委托并返回"外部"委托，形成洋葱式中间件层次。`runAsync()` 在构建前自动调用 `useOf(request.getClass(), true)` 将上下文的 `@PipelineBehaviors` 注入管道头部。

---

### PipelineDelegate\<C, R\>

> `@FunctionalInterface` — 函数式接口，表示管道中"下一个"处理节点。

#### invoke(C context) → CompletionStage\<R\>

异步调用管道委托。

- **Parameters**:
  - `context` (`C`): 请求/上下文对象
- **Returns**: `CompletionStage<R>` — 异步执行结果

---

### PipelineBehavior\<C, R\>

> `interface` — 定义了管道行为的接口，表示在管道中处理请求的单个中间件组件。

#### handleAsync(C context, PipelineDelegate\<C, R\> next) → CompletionStage\<R\>

异步处理请求。通过在返回前/后执行代码实现 AOP 风格拦截。

- **Parameters**:
  - `context` (`C`): 请求/上下文对象
  - `next` (`PipelineDelegate<C, R>`): 下一个管道委托
- **Returns**: `CompletionStage<R>` — 异步执行结果

---

### @PipelineBehaviors

> `annotation` `@Retention(RUNTIME) @Target(TYPE)` — 用于标记一个类，指定与该类相关的管道行为组件。

| 元素 | 类型 | 默认值 | 描述 |
|------|------|--------|------|
| `value` | `Class<?>[]` | (required) | 与该类相关的管道行为组件的类型数组 |

---

### PipelineFactory

> `interface` — 负责创建 Pipeline 实例的工厂接口，抽象创建逻辑。

#### \<C, R\> create() → Pipeline\<C, R\>

创建一个新的 Pipeline 实例。

- **Returns**: `Pipeline<C, R>` — 新的 Pipeline 实例

---

### DefaultPipelineFactory

> `class` `implements PipelineFactory` — PipelineFactory 的默认实现，使用 ServiceProvider 来解析和实例化管道组件。

#### DefaultPipelineFactory(ServiceProvider provider)

构造函数。

- **Parameters**:
  - `provider` (`ServiceProvider`): 用于解析和实例化管道组件的 ServiceProvider

#### \<C, R\> create() → Pipeline\<C, R\>

创建一个新的 Pipeline 实例。返回一个基于 `DefaultPipelineProvider` 的新管道。

---

### DefaultPipelineProvider\<C, R\>

> `class` `extends PipelineBase<C, R>` — Pipeline 的具体实现，使用反射来调用管道行为。同时支持同步和异步的 handle 方法，以及实现了 PipelineBehavior 接口的行为。

| 字段 | 类型 | 描述 |
|------|------|------|
| `HANDLE_METHOD_NAME` | `static final String` | 同步处理方法名：`"handle"` |
| `HANDLE_METHOD_NAME_ASYNC` | `static final String` | 异步处理方法名：`"handleAsync"` |
| `provider` | `ServiceProvider` | 服务提供者，用于解析和创建行为实例 |

#### DefaultPipelineProvider(ServiceProvider provider)

使用指定的服务提供者构造管道提供者。

- **Parameters**:
  - `provider` (`ServiceProvider`): 服务提供者

#### getNext(PipelineDelegate next, Class\<?\> behaviorType, Object... args) → PipelineDelegate

获取下一个管道委托。如果行为类型实现了 `PipelineBehavior` 接口，则直接调用其异步处理方法；否则使用反射查找 `handle` / `handleAsync` 方法进行调用。

- **Returns**: `PipelineDelegate<C, R>` — 包装了行为调用的管道委托

---

## 依赖

- `com.euonia:core` (compile)
- `org.junit.jupiter:junit-jupiter` (test)

## 作者

damon (zhaorong@outlook.com)
