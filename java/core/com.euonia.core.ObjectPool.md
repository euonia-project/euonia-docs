# ObjectPool

> 对象池接口，定义了获取池容量、关联的策略以及获取和释放对象的方法。

- **Module**: `core`
- **Type**: `interface`
- **Package**: `com.euonia.core`
- **Author**: damon(zhaorong@outlook.com)

## Type Parameters

| Parameter | Bound | Description |
|-----------|-------|-------------|
| `T` | *(无)* | 池管理的对象类型 |

## Methods

### getCapacity

> 获取对象池的容量，即池中可以同时存在的最大对象数量。

- **Returns**: `int` - 对象池的容量

### getPolicy

> 获取与对象池关联的策略。

- **Returns**: `ObjectPoolPolicy<T>` - 对象池策略

### acquire

> 获取一个对象池中的对象。

- **Returns**: `T` - 对象池中的对象

### release

> 释放一个对象池中的对象，将其返回到池中。

- **Parameters**:
  - `obj` (`T`): 要释放的对象
