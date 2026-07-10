# UseCasePresenter

> 用例呈现器，实现了用例的输出端口，允许订阅者监听成功和失败事件。同时实现了 {@link UseCaseSuccess}、{@link UseCaseFailure} 和 {@link AutoCloseable} 接口，基于 {@link SubmissionPublisher} 实现响应式的事件传递。

- **Type**: class
- **Package**: `com.euonia.usecase`
- **Author**: damon(zhaorong@outlook.com)
- **Implements**: `UseCaseSuccess<O>`, `UseCaseFailure`, `AutoCloseable`

## Type Parameters

| Parameter | Description |
|-----------|-------------|
| `O` | 用例成功输出的类型 |

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `publisher` | `Publisher<O>` | 事件发布者，用于向订阅者推送成功/失败事件 |
| `output` | `O` | 用例执行的成功输出 |

## Methods

### subscribe

> 订阅呈现器以接收成功和失败事件。

- **Parameters**:
  - `onSuccess` (`Consumer<O>`): 用于处理成功输出的消费者
  - `onFailure` (`Consumer<Throwable>`): 用于处理错误的消费者

### success

> 表示用例执行已成功并返回结果。将输出存储并提交给订阅者。

- **Parameters**:
  - `output` (`O`): 成功执行的结果

### error

> 表示用例执行因错误而失败。通过 publisher 异常关闭通知订阅者。

- **Parameters**:
  - `throwable` (`Throwable`): 导致失败的异常

### close

> 关闭呈现器，释放 publisher 资源。

### getOutput

> 返回用例执行成功时的输出。

- **Returns**: `O` - 用例执行的输出
