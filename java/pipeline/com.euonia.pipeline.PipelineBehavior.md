# PipelineBehavior

> PipelineBehavior 定义了管道行为的接口，表示在管道中处理请求的组件。它包含一个 handleAsync 方法，该方法接收请求对象和 PipelineDelegate，并返回一个表示异步执行结果的 CompletionStage。

- **Type**: interface
- **Package**: `com.euonia.pipeline`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<C>` — 请求/上下文对象的类型，`<R>` — 响应对象的类型

## Methods

### handleAsync

> 异步处理请求的方法。

- **Parameters**:
  - `context` (`C`): 请求/上下文对象
  - `next` (`PipelineDelegate<C, R>`): 下一个管道委托
- **Returns**: `CompletionStage<R>` — 表示异步执行结果的 CompletionStage
