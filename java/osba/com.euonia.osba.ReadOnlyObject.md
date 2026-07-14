# ReadOnlyObject

> 表示一个只读的业务对象。该类继承自 BusinessObject，适用于创建后不应被修改的对象。它不提供任何额外的方法或属性，但作为一个标记，用于指示该对象是只读的。

- **Type**: abstract class
- **Package**: `com.euonia.osba`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<T extends ReadOnlyObject<T>>` — 业务对象的类型，必须继承自 ReadOnlyObject
- **Extends**: `BusinessObject<T>`

## Methods

### `<V> getProperty(String propertyName, V field, V defaultValue): V`

> 获取属性的值。如果对象未绕过规则检查且属性不可读，则该方法将返回指定的默认值。

**Parameters:**
- `propertyName` (`String`): 属性名称
- `field` (`V`): 属性的当前值
- `defaultValue` (`V`): 属性的默认值，如果对象未绕过规则检查且属性不可读，则返回该值

**Returns:** `V` — 属性的值，如果对象未绕过规则检查且属性不可读，则返回 defaultValue

### `<V> getProperty(PropertyInfo<V> propertyInfo, V field): V`

> 获取属性的值。如果对象未绕过规则检查且属性不可读，则该方法将返回属性的默认值。

**Parameters:**
- `propertyInfo` (`PropertyInfo<V>`): 属性信息
- `field` (`V`): 属性的当前值

**Returns:** `V` — 属性的值，如果对象未绕过规则检查且属性不可读，则返回属性的默认值

### `<V> getProperty(PropertyInfo<V> propertyInfo, V field, V defaultValue): V`

> 获取属性的值。如果对象未绕过规则检查且属性不可读，则该方法将返回指定的默认值。

**Parameters:**
- `propertyInfo` (`PropertyInfo<V>`): 属性信息
- `field` (`V`): 属性的当前值
- `defaultValue` (`V`): 属性的默认值，如果对象未绕过规则检查且属性不可读，则返回该值

**Returns:** `V` — 属性的值，如果对象未绕过规则检查且属性不可读，则返回 defaultValue

### `<V> getProperty(PropertyInfo<V> propertyInfo): V`

> 获取属性的值。如果对象未绕过规则检查且属性不可读，则该方法将返回属性的默认值。

**Parameters:**
- `propertyInfo` (`PropertyInfo<V>`): 属性信息

**Returns:** `V` — 属性的值

### `<V> setProperty(PropertyInfo<V> propertyInfo, V newValue): void`

> 设置属性的值。如果对象未绕过规则检查且属性不可写入，则该方法将直接返回而不做任何更改。

**Parameters:**
- `propertyInfo` (`PropertyInfo<V>`): 属性信息
- `newValue` (`V`): 要设置的新值
