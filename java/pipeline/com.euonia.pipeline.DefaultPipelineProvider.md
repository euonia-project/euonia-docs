# DefaultPipelineProvider

> DefaultPipelineProvider 是 Pipeline 的具体实现，使用反射来调用管道行为。它同时支持同步和异步的 handle 方法，以及实现了 PipelineBehavior 接口的行为。

- **Type**: class
- **Package**: `com.euonia.pipeline`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<C>` — 请求/上下文对象的类型，`<R>` — 响应对象的类型
- **Extends**: `PipelineBase<C, R>`

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `HANDLE_METHOD_NAME` | `String` | 同步处理方法名：`"handle"` |
| `HANDLE_METHOD_NAME_ASYNC` | `String` | 异步处理方法名：`"handleAsync"` |
| `provider` | `ServiceProvider` | 服务提供者，用于解析和创建行为实例 |

## Methods

### DefaultPipelineProvider (constructor)

> 使用指定的服务提供者构造管道提供者。

- **Parameters**:
  - `provider` (`ServiceProvider`): 服务提供者

### getNext

> 获取下一个管道委托。如果行为类型实现了 PipelineBehavior 接口，则直接调用其异步处理方法；否则使用反射查找 handle/handleAsync 方法进行调用。

- **Parameters**:
  - `next` (`PipelineDelegate<C, R>`): 链中的下一个委托
  - `behaviorType` (`Class<?>`): 行为类型
  - `constructorArguments` (`Object...`): 构造参数，next 委托会被自动添加到参数列表开头
- **Returns**: `PipelineDelegate<C, R>` — 包装了行为调用的管道委托

### invokeTyped

> 通过反射调用行为方法，自动解析除第一个参数（请求）之外的所有方法参数。如果方法返回值是 CompletionStage，则返回异步结果；否则返回已完成的空 CompletableFuture。

- **Parameters**:
  - `method` (`Method`): 要调用的方法
  - `instance` (`Object`): 行为实例
  - `request` (`C`): 请求对象
- **Returns**: `CompletionStage<R>` — 包含方法返回值的完成阶段

### resolveHandleMethod

> 在给定的行为类型中查找 handle 或 handleAsync 方法。若同时存在两个方法，选取参数个数较少的那个。

- **Parameters**:
  - `behaviorType` (`Class<?>`): 要搜索的行为类型
- **Returns**: `Method` — 匹配的方法
- **Throws**: `IllegalStateException` 如果未找到或找到多个匹配的方法

### castType

> 安全地将 `Class<?>` 转换为 `Class<T>`，避免原始类型警告。

- **Type Parameters**: `<T>` — 目标类型
- **Parameters**:
  - `type` (`Class<?>`): 要转换的类类型
- **Returns**: `Class<T>` — 转换后的类型

### prepend

> 将一个元素前置添加到数组的开头。

- **Parameters**:
  - `first` (`Object`): 要放在数组开头的元素
  - `rest` (`Object[]`): 原始数组
- **Returns**: `Object[]` — 包含 first 后跟 rest 所有元素的新数组
