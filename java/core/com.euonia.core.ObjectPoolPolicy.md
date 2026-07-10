# ObjectPoolPolicy

> ObjectPoolPolicy 是一个定义对象池行为的接口。它指定了对象池如何创建、验证和销毁对象，以及当所有对象都在使用中时池应该如何处理。

- **Type**: interface
- **Package**: `com.euonia.core`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### create

> 创建对象的方法。当池需要一个新对象时调用。

- **Returns**: `T` - 创建的新对象

### validate

> 验证对象的方法。当对象被从池中获取时调用，以确保它仍然有效。

- **Parameters**:
  - `obj` (`T`): 要验证的对象
- **Returns**: `boolean` - true 如果对象有效且可以被重用，否则返回 false

### destroy

> 销毁对象的方法。当对象被从池中移除时调用，以执行任何必要的清理操作。

- **Parameters**:
  - `obj` (`T`): 要销毁的对象

### oversizeBehavior

> 定义当对象池中的对象都在使用中时的行为。

- **Returns**: `OversizeBehavior` - 超过最大容量时的行为

## Inner Types

### OversizeBehavior

> 定义当对象池中的对象超过预设的最大容量时的行为。

- **Type**: enum

#### Enum Constants

| Constant | Description |
|----------|-------------|
| `THROW_EXCEPTION` | 抛出异常 |
| `RETURN_NULL` | 返回 null |
| `CREATE_NEW` | 记录警告但继续运行 |
| `WAIT_FOR_AVAILABLE` | 等待直到有可用对象 |
