# PropertyInfoList

> PropertyInfoList 是一个扩展自 ArrayList 的类，用于存储 PropertyInfo 对象。它提供了一个线程安全的方法 getOrAdd 来获取或添加 PropertyInfo。该类还包含一个 Semaphore 用于控制对列表的访问，以确保线程安全。此外，它还具有锁定机制，可以通过 lock 和 unlock 方法来控制列表的修改权限。

- **Type**: class
- **Package**: `com.euonia.reflection`
- **Author**: damon(zhaorong@outlook.com)
- **Extends**: `ArrayList<PropertyInfo<?>>`

## Constructors

### PropertyInfoList

> 创建一个新的 PropertyInfoList 实例。

### PropertyInfoList

> 使用指定的列表创建一个新的 PropertyInfoList 实例。

- **Parameters**:
  - `list` (`List<PropertyInfo<?>>`): 要包含的 PropertyInfo 对象列表

## Methods

### isLocked

> 判断列表是否被锁定。

- **Returns**: `boolean` — 如果列表被锁定，则返回 true，否则返回 false

### lock

> 锁定列表，禁止修改。

### unlock

> 解锁列表，允许修改。

### getOrAdd

> 获取或添加 PropertyInfo 对象。使用信号量保证线程安全。

- **Parameters**:
  - `propertyInfo` (`PropertyInfo<?>`): 要获取或添加的 PropertyInfo 对象
- **Returns**: `PropertyInfo<?>` — 已存在的 PropertyInfo 对象或新添加的 PropertyInfo 对象
