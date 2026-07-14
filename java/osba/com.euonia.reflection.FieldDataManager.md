# FieldDataManager

> FieldDataManager 是一个管理业务对象字段数据的类。它维护一个字段数据的映射，并提供方法来获取、创建、设置和加载字段数据。该类还提供了一个静态方法来初始化业务对象类型的静态字段，以确保所有静态属性都被注册。

- **Type**: class
- **Package**: `com.euonia.reflection`
- **Author**: damon(zhaorong@outlook.com)

## Constructors

### `FieldDataManager(Class<?> businessObjectType)`
> 使用指定的业务对象类型构造一个新的 FieldDataManager 实例，创建包含该类型及其所有父类属性的合并列表。

**Parameters:**
- `businessObjectType` (`Class<?>`): 业务对象类型

## Methods

### `getRegisteredProperties(): List<PropertyInfo<?>>`
> 获取已注册的属性列表。

**Returns:** `List<PropertyInfo<?>>` — 已注册的属性列表

### `getRegisteredProperty(String propertyName): PropertyInfo<?>`
> 获取指定名称的已注册属性。

**Parameters:**
- `propertyName` (`String`): 属性名称

**Returns:** `PropertyInfo<?>` — 已注册的属性

**Throws:** `IllegalArgumentException` — 如果属性未注册

### `getFieldData(String fieldName): FieldData<?>`
> 获取指定字段名称的字段数据。

**Parameters:**
- `fieldName` (`String`): 字段名称

**Returns:** `FieldData<?>` — 指定字段名称的字段数据，如果不存在则返回 null

### `getFieldData(PropertyInfo<T> property): FieldData<T>`
> 获取指定属性的字段数据。

**Parameters:**
- `property` (`PropertyInfo<T>`): 属性信息

**Returns:** `FieldData<T>` — 指定属性的字段数据

### `getOrCreateFieldData(PropertyInfo<T> property): FieldData<T>`
> 检索指定属性的字段数据，如果尚不存在则创建。此方法是同步的，以确保在访问和修改字段数据映射时的线程安全。

**Parameters:**
- `property` (`PropertyInfo<T>`): 要检索或创建字段数据的属性

**Returns:** `FieldData<T>` — 指定属性的字段数据

### `setFieldData(PropertyInfo<T> property, T value): void`
> 为指定的属性和值设置字段数据，如果字段数据尚不存在则创建。此方法是同步的，以确保在访问和修改字段数据映射时的线程安全。

**Parameters:**
- `property` (`PropertyInfo<T>`): 要设置字段数据的属性
- `value` (`T`): 要为字段数据设置的值

### `loadFieldData(PropertyInfo<T> property, T value): FieldData<T>`
> 加载指定属性和值的字段数据，并将其标记为未更改。

**Parameters:**
- `property` (`PropertyInfo<T>`): 要加载字段数据的属性
- `value` (`T`): 要为字段数据设置的值

**Returns:** `FieldData<T>` — 已加载的字段数据

### `removeFieldData(PropertyInfo<?> property): void`
> 移除与指定属性关联的字段数据（如果存在）。

**Parameters:**
- `property` (`PropertyInfo<?>`): 要移除字段数据的属性

### `fieldExists(String fieldName): boolean`
> 检查指定字段名称的字段数据是否存在。

**Parameters:**
- `fieldName` (`String`): 要检查的字段名称

**Returns:** `boolean` — 如果指定字段名称的字段数据存在则返回 true，否则返回 false

### `fieldExists(PropertyInfo<?> property): boolean`
> 检查指定属性的字段数据是否存在。

**Parameters:**
- `property` (`PropertyInfo<?>`): 要检查的属性

**Returns:** `boolean` — 如果指定属性的字段数据存在则返回 true，否则返回 false

### `isBusy(): boolean`
> 检查是否有任何字段数据处于忙碌状态。

**Returns:** `boolean` — 如果有任何字段数据处于忙碌状态则返回 true，否则返回 false

## Static Methods

### `initStaticFields(Class<?> businessObjectType): void`
> 初始化指定业务对象类型的静态字段，以确保所有静态属性都被注册。

**Parameters:**
- `businessObjectType` (`Class<?>`): 要为其初始化静态字段的业务对象类型
