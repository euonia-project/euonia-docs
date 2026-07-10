# SavedEventArgs

> 表示一个保存事件的参数类，包含保存操作的结果信息，如新对象、错误信息和用户状态。

- **Type**: class
- **Package**: `com.euonia.osba`
- **Author**: damon(zhaorong@outlook.com)

## Constructors

### SavedEventArgs

> 创建一个新的 SavedEventArgs 实例，包含保存操作的结果信息。

- **Parameters**:
  - `newObject` (`Object`): 保存操作生成的新对象

### SavedEventArgs

> 创建一个新的 SavedEventArgs 实例，包含保存操作的结果信息和用户状态。

- **Parameters**:
  - `newObject` (`Object`): 保存操作生成的新对象
  - `error` (`Throwable`): 保存操作过程中发生的错误
  - `userState` (`Object`): 用户状态信息

## Methods

### getNewObject

> 获取保存操作生成的新对象。

- **Returns**: `Object` — 保存操作生成的新对象

### getError

> 获取保存操作过程中发生的错误信息，如果没有错误则返回 null。

- **Returns**: `Throwable` — 保存操作过程中发生的错误信息，如果没有错误则返回 null

### getUserState

> 获取与保存操作相关的用户状态信息，可以用于在保存完成后执行特定的用户界面更新或其他操作。

- **Returns**: `Object` — 与保存操作相关的用户状态信息
