# Pipeline

> Pipeline 接口定义了构建和执行组件管道的契约，这些组件可以处理请求并生成响应。它允许向管道添加组件、构建管道以及使用给定的请求异步运行管道。组件可以按特定顺序或根据其类型添加，管道可以使用可选的累积函数来执行，以合并多个组件的结果。

- **Type**: interface
- **Package**: `com.euonia.pipeline`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<C>` — 请求/上下文对象的类型，`<R>` — 响应对象的类型

## Methods

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

> 根据上下文类型向管道添加组件。组件可以添加在其他组件之前。

- **Parameters**:
  - `contextType` (`Class<?>`): 组件的上下文类型
  - `useAheadOfOthers` (`boolean`): 是否将组件添加在其他组件之前
- **Returns**: `Pipeline<C, R>` — 当前管道实例

### build

> 构建管道并返回 PipelineDelegate。

- **Returns**: `PipelineDelegate<C, R>` — 构建好的 PipelineDelegate

### runAsync

> 使用给定的请求异步运行管道。

- **Parameters**:
  - `request` (`C`): 要通过管道传递的请求对象
- **Returns**: `CompletionStage<R>` — 表示异步执行结果的 CompletionStage

### runAsync

> 使用给定的请求和累积函数异步运行管道。

- **Parameters**:
  - `request` (`C`): 要通过管道传递的请求对象
  - `accumulate` (`Function<C, CompletionStage<R>>`): 用于累积多个组件结果的函数
- **Returns**: `CompletionStage<R>` — 表示异步执行结果的 CompletionStage
