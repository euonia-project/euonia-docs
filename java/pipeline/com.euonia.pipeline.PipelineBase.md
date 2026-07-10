# PipelineBase

> PipelineBase 是 Pipeline 接口的抽象实现，提供了构建和执行组件管道的基本功能。它维护一个组件列表，这些组件定义了管道中处理请求的行为。组件可以通过 use 方法添加到管道中，并且可以按特定顺序或根据其类型添加。build 方法构建管道，将组件组合成一个 PipelineDelegate 实例，runAsync 方法使用给定的请求异步运行管道，并可选地使用累积函数来合并多个组件的结果。

- **Type**: abstract class
- **Package**: `com.euonia.pipeline`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<C>` — 请求/上下文对象的类型，`<R>` — 响应对象的类型
- **Implements**: `Pipeline<C, R>`

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `components` | `List<Function<PipelineDelegate<C, R>, PipelineDelegate<C, R>>>` | 存储管道组件的列表 |

## Methods

### getComponents

> 获取管道中组件的列表。返回一个不可修改的列表。

- **Returns**: `List<Function<PipelineDelegate<C, R>, PipelineDelegate<C, R>>>` — 管道中组件的列表

### use

> 向管道添加组件。该组件定义为一个函数，接收 PipelineDelegate 并返回 PipelineDelegate。

- **Parameters**:
  - `component` (`Function<PipelineDelegate<C, R>, PipelineDelegate<C, R>>`): 要添加到管道的组件
- **Returns**: `Pipeline<C, R>` — 当前管道实例

### use

> 在指定索引位置向管道添加组件。该组件定义为一个函数，接收 PipelineDelegate 并返回 PipelineDelegate。

- **Parameters**:
  - `component` (`Function<PipelineDelegate<C, R>, PipelineDelegate<C, R>>`): 要添加到管道的组件
  - `index` (`int`): 添加组件的索引位置
- **Returns**: `Pipeline<C, R>` — 当前管道实例

### use

> 向管道添加组件。该组件定义为一个 BiFunction，接收请求对象和 PipelineDelegate，并返回响应的 CompletionStage。

- **Parameters**:
  - `handler` (`BiFunction<C, PipelineDelegate<C, R>, CompletionStage<R>>`): 要添加到管道的处理器
- **Returns**: `Pipeline<C, R>` — 当前管道实例

### use

> 根据类型向管道添加组件。组件定义为一个类和可选的参数。

- **Parameters**:
  - `type` (`Class<?>`): 要添加的组件的类类型
  - `args` (`Object...`): 组件构造函数的可选参数
- **Returns**: `Pipeline<C, R>` — 当前管道实例

### useOf

> 根据上下文类型向管道添加组件。组件可以添加在其他组件之前。从 `@PipelineBehaviors` 注解读取关联的行为组件类型并添加。

- **Parameters**:
  - `contextType` (`Class<?>`): 组件的上下文类型
  - `useAheadOfOthers` (`boolean`): 是否将组件添加在其他组件之前
- **Returns**: `Pipeline<C, R>` — 当前管道实例

### build

> 构建管道并返回 PipelineDelegate。将组件列表反转后依次应用，构建最终的管道委托链。构建完成后清除组件列表。

- **Returns**: `PipelineDelegate<C, R>` — 构建好的 PipelineDelegate

### runAsync

> 使用给定的请求异步运行管道。自动将请求类型的关联行为组件添加到管道头部，然后构建并执行。

- **Parameters**:
  - `request` (`C`): 要通过管道传递的请求对象
- **Returns**: `CompletionStage<R>` — 表示异步执行结果的 CompletionStage

### runAsync

> 使用给定的请求和累积函数异步运行管道。累积函数用于合并多个组件的结果。

- **Parameters**:
  - `request` (`C`): 要通过管道传递的请求对象
  - `accumulate` (`Function<C, CompletionStage<R>>`): 用于合并多个组件结果的函数
- **Returns**: `CompletionStage<R>` — 表示异步执行结果的 CompletionStage

### getNext

> 获取下一个 PipelineDelegate 实例，基于指定的类型和构造函数参数创建组件实例。

- **Parameters**:
  - `next` (`PipelineDelegate<C, R>`): 下一个 PipelineDelegate 实例
  - `type` (`Class<?>`): 组件的类类型
  - `constructorArguments` (`Object...`): 组件构造函数的参数
- **Returns**: `PipelineDelegate<C, R>` — 包含新组件的 PipelineDelegate 实例
