# PipelineDelegate

> PipelineDelegate 定义了管道委托的接口，表示在管道中处理请求的组件。它包含一个 invoke 方法，该方法接收请求对象并返回一个表示异步执行结果的 CompletionStage。

- **Type**: interface (FunctionalInterface)
- **Package**: `com.euonia.pipeline`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<C>` — 请求/上下文对象的类型，`<R>` — 响应对象的类型

## Methods

### invoke

> 异步调用管道委托的方法。

- **Parameters**:
  - `context` (`C`): 请求/上下文对象
- **Returns**: `CompletionStage<R>` — 表示异步执行结果的 CompletionStage
