# ObservableObject

> 表示一个可观察的业务对象，能够跟踪其编辑状态（新建、已修改、已删除）并管理其忙碌状态。该类提供方法来标记对象为新建、已修改或已删除，以及检查对象是否忙碌或可保存。它还实现了遵循对象规则和权限的属性访问方法。

- **Type**: abstract class
- **Package**: `com.euonia.osba`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<T extends ObservableObject<T>>` — 可观察对象的类型
- **Extends**: `BusinessObject<T>`
- **Implements**: `TrackableObject`, `OperableProperty`

## Methods

### getState

> 获取对象的当前编辑状态，指示对象是新建、已修改还是已删除。

- **Returns**: `ObjectEditState` — 对象的当前编辑状态

### isNew

> 检查对象是否为新建状态，即已创建但尚未保存到数据库。

- **Returns**: `boolean` — 如果对象为新建则返回 true，否则返回 false

### isChanged

> 检查对象是否已被修改，即自上次保存到数据库以来已被修改。

- **Returns**: `boolean` — 如果对象已被修改则返回 true，否则返回 false

### isDeleted

> 检查对象是否已被标记为删除，即已被标记待删除但尚未从数据库中移除。

- **Returns**: `boolean` — 如果对象已被标记为删除则返回 true，否则返回 false

### isCheckObjectRulesOnDelete

> 返回一个值用于判断当对象被标记为删除时是否应检查对象规则。此标志可在标记对象为删除时设置，以指示在允许删除操作继续之前是否应评估任何业务规则。

- **Returns**: `boolean` — 如果删除时应检查对象规则则返回 true，否则返回 false

### markAsNew

> 将对象标记为新建，表示该对象已创建但尚未保存到数据库。此方法将对象的编辑状态设置为 NEW，可用于跟踪变更并判断对象是否需要保存。

### markAsChanged

> 将对象标记为已修改，表示该对象自上次保存到数据库以来已被修改。此方法将对象的编辑状态设置为 CHANGED，可用于跟踪变更并判断对象是否需要保存。

### markAsDeleted

> 将对象标记为删除，表示该对象已被标记待删除但尚未从数据库中移除。此方法将对象的编辑状态设置为 DELETED，可用于跟踪变更并判断对象是否需要删除。

### markAsDeleted

> 将对象标记为删除，表示该对象已被标记待删除但尚未从数据库中移除。此方法将对象的编辑状态设置为 DELETED，可用于跟踪变更并判断对象是否需要删除。

- **Parameters**:
  - `checkObjectRules` (`boolean`): 在允许删除操作继续之前是否检查对象规则

### isBusy

> 检查对象当前是否忙碌，即是否正在执行阻止其被保存或修改的操作。此方法同时检查对象自身的忙碌状态以及任何关联字段或规则的忙碌状态，以判断对象当前是否忙碌。

- **Returns**: `boolean` — 如果对象忙碌则返回 true，否则返回 false

### isSelfBusy

> 检查对象自身是否忙碌，即是否正在执行阻止其被保存或修改的操作。此方法检查对象自身的忙碌状态以及正在运行的规则的忙碌状态，以判断对象当前是否忙碌。

- **Returns**: `boolean` — 如果对象自身忙碌则返回 true，否则返回 false

### isSavable

> 检查对象是否可保存，即对象是否有效、有变更且不忙碌。此方法可用于判断对象是否可以保存到数据库。

- **Returns**: `boolean` — 如果对象可保存则返回 true，否则返回 false

### markAsBusy

> 将对象标记为忙碌，表示该对象正在执行阻止其被保存或修改的操作。此方法递增忙碌计数器，并在对象变为忙碌时通知所有监听器。

### markAsIdle

> 将对象标记为空闲，表示该对象不再执行阻止其被保存或修改的操作。此方法递减忙碌计数器，并在对象变为空闲时通知所有监听器。

### onBusyChanged

> 订阅一个监听器，当对象的忙碌状态发生变化时接收通知。

- **Parameters**:
  - `listener` (`Consumer<Boolean>`): 要通知的监听器

### addBusyChangedListener

> 添加一个监听器，当对象的忙碌状态发生变化时接收通知。

- **Parameters**:
  - `listener` (`Consumer<Boolean>`): 要通知的监听器

### removeBusyChangedListener

> 移除一个监听器，不再接收对象忙碌状态变化的通知。

- **Parameters**:
  - `listener` (`Consumer<Boolean>`): 要移除的监听器

### getProperty

> 获取属性值，遵循对象规则和权限。

- **Parameters**:
  - `propertyName` (`String`): 属性名称
  - `field` (`V`): 当前字段值
  - `defaultValue` (`V`): 默认值
- **Returns**: `V` — 属性值，如果无法读取属性则返回默认值

### getProperty

> 获取属性值，遵循对象规则和权限。

- **Parameters**:
  - `propertyInfo` (`PropertyInfo<V>`): 属性信息
  - `field` (`V`): 当前字段值
- **Returns**: `V` — 属性值，如果无法读取属性则返回默认值

### getProperty

> 获取属性值，遵循对象规则和权限。

- **Parameters**:
  - `propertyInfo` (`PropertyInfo<V>`): 属性信息
  - `field` (`V`): 当前字段值
  - `defaultValue` (`V`): 默认值
- **Returns**: `V` — 属性值，如果无法读取属性则返回默认值

### getProperty

> 获取属性值，遵循对象规则和权限。

- **Parameters**:
  - `property` (`PropertyInfo<V>`): 要获取值的属性信息
- **Returns**: `V` — 属性值，如果无法读取属性则返回属性的默认值

### setProperty

> 设置属性值，遵循对象规则和权限。

- **Parameters**:
  - `property` (`PropertyInfo<V>`): 要设置值的属性信息
  - `newValue` (`V`): 要设置的新值
