# PropertyInfoManager

> PropertyInfoManager 是一个管理业务对象属性信息的类。它维护一个属性信息的缓存，并提供方法来获取、注册和查询属性信息。该类使用 ConcurrentHashMap 来存储不同类型的属性信息列表，并通过 computeIfAbsent 方法确保每个类型只有一个属性信息列表被创建。

- **Type**: class
- **Package**: `com.euonia.reflection`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### getPropertyListCache

> 获取指定类型的属性信息列表。如果列表不存在，则创建一个新的列表并缓存。

- **Parameters**:
  - `type` (`Type`): 要获取属性信息的类型
- **Returns**: `PropertyInfoList` — 指定类型的属性信息列表

### getRegisteredProperties

> 获取指定类型的已注册属性信息列表。

- **Parameters**:
  - `type` (`Type`): 要获取已注册属性信息的类型
- **Returns**: `PropertyInfoList` — 指定类型的已注册属性信息列表

### getRegisteredProperty

> 获取指定类型和属性名称的已注册属性信息。

- **Parameters**:
  - `type` (`Type`): 要获取已注册属性信息的类型
  - `propertyName` (`String`): 要获取已注册属性信息的属性名称
- **Returns**: `PropertyInfo` — 指定类型和属性名称的已注册属性信息，如果不存在则返回 null

### registerProperty

> 注册一个新的属性信息。如果属性信息已存在，则返回现有的属性信息。

- **Parameters**:
  - `type` (`Type`): 要注册属性信息的类型
  - `propertyInfo` (`PropertyInfo<?>`): 要注册的属性信息
- **Returns**: `PropertyInfo<?>` — 注册后的属性信息，如果属性信息已存在，则返回现有的属性信息
