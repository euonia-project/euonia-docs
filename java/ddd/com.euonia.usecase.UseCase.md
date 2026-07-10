# UseCase

> 表示应用中的一个用例。用例是可以在系统内执行的特定操作或动作，定义了执行特定业务逻辑或功能的契约。

- **Type**: interface
- **Package**: `com.euonia.usecase`
- **Author**: damon(zhaorong@outlook.com)

## Type Parameters

| Parameter | Description |
|-----------|-------------|
| `I` | 用例输入的类型 |
| `O` | 用例输出的类型 |

## Methods

### execute

> 使用给定的输入执行用例并返回输出。

- **Parameters**:
  - `input` (`I`): 用例的输入数据
- **Returns**: `O` - 用例的输出数据
