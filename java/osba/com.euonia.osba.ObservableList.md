# ObservableList

> 可观察列表，提供子属性通知、集合变更通知以及聚合忙碌状态通知。

- **Type**: class
- **Package**: `com.euonia.osba`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<TItem>` — 列表项类型
- **Extends**: `ArrayList<TItem>`

## Constructors

### ObservableList

> 创建一个新的 ObservableList 实例，初始为空。

### ObservableList

> 创建一个新的 ObservableList 实例，并使用指定的集合初始化列表。

- **Parameters**:
  - `items` (`Collection<? extends TItem>`): 初始化列表的集合

## Methods

### isRaiseListChangedEvents

> 获取一个值，指示是否在列表项属性更改或集合结构更改时引发事件。

- **Returns**: `boolean` — 如果在列表项属性更改或集合结构更改时引发事件，则返回 true；否则返回 false

### setRaiseListChangedEvents

> 设置一个值，指示是否在列表项属性更改或集合结构更改时引发事件。

- **Parameters**:
  - `raiseListChangedEvents` (`boolean`): 如果在列表项属性更改或集合结构更改时引发事件，则为 true；否则为 false

### addChildChangedListener

> 订阅子属性变更事件。当列表项的属性发生更改时，将触发此事件。

- **Parameters**:
  - `listener` (`Consumer<ObjectChangedEventArgs>`): 事件监听器

### removeChildChangedListener

> 取消订阅子属性变更事件。

- **Parameters**:
  - `listener` (`Consumer<ObjectChangedEventArgs>`): 事件监听器

### addItemPropertyChangedListener

> 订阅列表中各项的属性变更事件。事件参数的 `propertyChangedEvent` 为非空，`collectionChangeType` 为空。

- **Parameters**:
  - `listener` (`Consumer<ObjectChangedEventArgs>`): 事件监听器

### removeItemPropertyChangedListener

> 取消订阅列表中各项的属性变更事件。

- **Parameters**:
  - `listener` (`Consumer<ObjectChangedEventArgs>`): 事件监听器

### addCollectionChangedListener

> 订阅集合结构变更事件（添加、移除、替换、清空）。事件参数的 `collectionChangeType` 为非空，`propertyChangedEvent` 为空。

- **Parameters**:
  - `listener` (`Consumer<ObjectChangedEventArgs>`): 事件监听器

### removeCollectionChangedListener

> 取消订阅集合结构变更事件。

- **Parameters**:
  - `listener` (`Consumer<ObjectChangedEventArgs>`): 事件监听器

### addBusyChangedListener

> 订阅忙碌状态变更事件。

- **Parameters**:
  - `listener` (`Consumer<Boolean>`): 事件监听器

### removeBusyChangedListener

> 取消订阅忙碌状态变更事件。

- **Parameters**:
  - `listener` (`Consumer<Boolean>`): 事件监听器

### isBusy

> 获取一个值，指示列表中是否有任何项处于忙碌状态。如果列表中的任何项是 TrackableObject 并且其 IsBusy 属性为 true，则返回 true；否则返回 false。

- **Returns**: `boolean` — 如果列表中有任何项处于忙碌状态，则返回 true；否则返回 false

### suppressListChangedEvents

> 在一个范围内暂时禁止引发列表项属性更改和集合结构更改事件。当返回的 AutoCloseable 对象被关闭时，将恢复事件引发。

- **Returns**: `AutoCloseable` — 一个 AutoCloseable 对象，用于在关闭时恢复事件引发

### add

> 将指定的元素添加到此列表的末尾，并引发相应的事件。

- **Parameters**:
  - `item` (`TItem`): 要添加到列表末尾的元素
- **Returns**: `boolean` — 如果列表因调用而发生更改，则返回 true；否则返回 false

### add

> 将指定的元素插入此列表中的指定位置，并引发相应的事件。

- **Parameters**:
  - `index` (`int`): 要插入元素的位置
  - `item` (`TItem`): 要插入的元素

### addAll

> 将指定的集合中的所有元素添加到此列表的末尾，并引发相应的事件。

- **Parameters**:
  - `items` (`Collection<? extends TItem>`): 要添加到列表末尾的元素集合
- **Returns**: `boolean` — 如果列表因调用而发生更改，则返回 true；否则返回 false

### addAll

> 将指定的集合中的所有元素插入此列表的指定位置，并引发相应的事件。

- **Parameters**:
  - `index` (`int`): 要插入元素的位置
  - `items` (`Collection<? extends TItem>`): 要插入的元素集合
- **Returns**: `boolean` — 如果列表因调用而发生更改，则返回 true；否则返回 false

### remove

> 从此列表中移除指定位置的元素，并引发相应的事件。

- **Parameters**:
  - `index` (`int`): 要移除元素的位置
- **Returns**: `TItem` — 被移除的元素

### remove

> 从此列表中移除指定的元素，并引发相应的事件。

- **Parameters**:
  - `item` (`Object`): 要移除的元素
- **Returns**: `boolean` — 如果列表因调用而发生更改，则返回 true；否则返回 false

### set

> 用指定的元素替换此列表中指定位置的元素，并引发相应的事件。

- **Parameters**:
  - `index` (`int`): 要替换元素的位置
  - `item` (`TItem`): 要存放在指定位置的元素
- **Returns**: `TItem` — 被替换的元素

### clear

> 从此列表中移除所有元素，并引发相应的事件。
