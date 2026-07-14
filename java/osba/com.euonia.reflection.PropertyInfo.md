# PropertyInfo

> 表示业务对象属性的元数据，包括其名称、类型、默认值和显示名称。

- **Type**: class
- **Package**: `com.euonia.reflection`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<T>` — 属性值的类型
- **Implements**: `Comparable<PropertyInfo<T>>`

## Constructors

### `PropertyInfo(Class<T> type, String name)`
> 创建一个新的 PropertyInfo 实例。

**Parameters:**
- `type` (`Class<T>`): 属性值的类型
- `name` (`String`): 属性的名称

### `PropertyInfo(Class<T> type, String name, String friendlyName, Supplier<T> defaultValue)`
> 创建一个新的 PropertyInfo 实例，包含显示名称和默认值。

**Parameters:**
- `type` (`Class<T>`): 属性值的类型
- `name` (`String`): 属性的名称
- `friendlyName` (`String`): 属性的显示名称
- `defaultValue` (`Supplier<T>`): 属性的默认值供应器

### `PropertyInfo(Class<T> type, String name, String friendlyName, Class<?> objectType, Supplier<T> defaultValue)`
> 创建一个新的 PropertyInfo 实例，包含显示名称、默认值和字段信息。

**Parameters:**
- `type` (`Class<T>`): 属性值的类型
- `name` (`String`): 属性的名称
- `friendlyName` (`String`): 属性的显示名称
- `objectType` (`Class<?>`): 包含此属性的对象类型，用于反射获取字段信息
- `defaultValue` (`Supplier<T>`): 属性的默认值供应器

## Methods

### `getName(): String`
> 获取属性的名称。

**Returns:** `String` — 属性的名称

### `getFriendlyName(): String`
> 获取属性的显示名称，如果未设置显示名称，则返回属性的名称。

**Returns:** `String` — 属性的显示名称或属性的名称

### `getDefaultValue(): T`
> 获取属性的默认值。

**Returns:** `T` — 属性的默认值

### `getType(): Class<T>`
> 获取属性的类型。

**Returns:** `Class<T>` — 属性的类型

### `isChild(): boolean`
> 判断属性是否为子对象。

**Returns:** `boolean` — 如果属性是子对象，则返回 true，否则返回 false

### `getField(): Field`
> 获取属性对应的字段信息。

**Returns:** `Field` — 属性的字段信息

### `newFieldData(String name): FieldData<T>`
> 创建一个新的 FieldData 实例。

**Parameters:**
- `name` (`String`): 字段的名称

**Returns:** `FieldData<T>` — 新的 FieldData 实例

### `compareTo(PropertyInfo<T> other): int`
> 比较当前 PropertyInfo 与另一个 PropertyInfo 的顺序。

**Parameters:**
- `other` (`PropertyInfo<T>`): 要比较的另一个 PropertyInfo

**Returns:** `int` — 一个负整数、零或一个正整数，分别表示当前 PropertyInfo 小于、等于或大于指定的 PropertyInfo
