# OperableProperty

> 表示一个可以获取和设置属性的对象的契约。

- **Type**: interface
- **Package**: `com.euonia.osba.abstracts`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### getProperty

> 根据提供的 PropertyInfo 获取属性的值。

- **Parameters**:
  - `propertyInfo` (`PropertyInfo<V>`): 表示要获取的属性的 PropertyInfo 对象
- **Returns**: `V` — 属性的值

### setProperty

> 根据提供的 PropertyInfo 和值设置属性的值。

- **Parameters**:
  - `propertyInfo` (`PropertyInfo<V>`): 表示要设置的属性的 PropertyInfo 对象
  - `value` (`V`): 要为属性设置的值
