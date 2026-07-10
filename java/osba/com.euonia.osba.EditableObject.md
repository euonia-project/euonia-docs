# EditableObject

> 表示可编辑的业务对象，可以保存到数据库或其他持久化存储中。此类继承 ObservableObject 并实现 Savable 接口，为 save 方法提供包含验证和事件处理的默认实现。

- **Type**: abstract class
- **Package**: `com.euonia.osba`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<T extends EditableObject<T>>` — 可编辑对象的类型
- **Extends**: `ObservableObject<T>`
- **Implements**: `Savable<T>`

## Methods

### onSaved

> 订阅 onSaved 事件的监听器，该事件在对象保存时触发。监听器将接收一个 SavedEventArgs 对象，其中包含已保存对象的信息、保存过程中发生的任何错误以及传递给 save 方法的任何用户状态。

- **Parameters**:
  - `listener` (`Consumer<SavedEventArgs>`): 对象保存时要通知的监听器

### onSaved

> 触发 onSaved 事件，通知所有订阅的监听器对象已保存。

- **Parameters**:
  - `newObject` (`T`): 已保存的对象
  - `error` (`Throwable`): 保存过程中发生的任何错误
  - `userState` (`Object`): 传递给 onSaved 事件的附加信息

### saveComplete

> 将当前对象保存到数据库或其他持久化存储中，并在保存完成后触发 onSaved 事件。

- **Parameters**:
  - `newObject` (`T`): 已保存的对象

### save

> 将当前对象保存到数据库或其他持久化存储中。

- **Parameters**:
  - `forceUpdate` (`boolean`): 是否强制更新，即使对象未被标记为已更改
- **Returns**: `T` — 已保存的对象

### save

> 将当前对象保存到数据库或其他持久化存储中。如果 forceUpdate 为 true，即使对象未被标记为已更改，也会保存该对象。userState 参数可用于向 onSaved 事件传递附加信息。

- **Parameters**:
  - `forceUpdate` (`boolean`): 是否强制更新，即使对象未被标记为已更改
  - `userState` (`Object`): 传递给 onSaved 事件的附加信息
- **Returns**: `T` — 已保存的对象

### create

> 预定义的create方法，子类可以覆盖此方法以实现对象的创建逻辑，例如设置初始属性值或触发创建事件。

### insert

> 预定义的insert方法，子类可以覆盖此方法以实现对象插入数据库或其他持久化存储的逻辑，例如执行数据库操作或触发插入事件。

### update

> 预定义的update方法，子类可以覆盖此方法以实现对象更新数据库或其他持久化存储的逻辑，例如执行数据库操作或触发更新事件。

### delete

> 预定义的delete方法，子类可以覆盖此方法以实现对象删除数据库或其他持久化存储的逻辑，例如执行数据库操作或触发删除事件。

### close

> 关闭资源，包括 savedEventPublisher。

### getSavedEventPublisher

> 获取保存事件发布器，使用 RequestContextAwareExecutor 作为执行器。

- **Returns**: `SubmissionPublisher<SavedEventArgs>` — 保存事件发布器
