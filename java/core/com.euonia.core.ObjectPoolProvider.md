# ObjectPoolProvider

> ObjectPoolProvider 是一个接口，定义了创建和管理对象池的方法。
> 它提供了根据给定的对象池策略创建对象池的功能，并允许指定池的容量。
> 此外，它还提供了一个方法来移除与特定策略关联的对象池。

- **Module**: `core`
- **Type**: `interface`
- **Package**: `com.euonia.core`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### create

> 根据提供的对象池策略创建一个对象池。这个方法使用默认容量创建池，并返回与策略关联的对象池实例。

- **Parameters**:
  - `policy` (`ObjectPoolPolicy<T>`): 对象池策略
- **Returns**: `ObjectPool<T>` - 与策略关联的对象池实例
- **Type Parameters**:
  - `T`: 池中对象的类型

### create

> 根据提供的对象池策略和指定的容量创建一个对象池。

- **Parameters**:
  - `policy` (`ObjectPoolPolicy<T>`): 对象池策略
  - `size` (`int`): 对象池的容量
- **Returns**: `ObjectPool<T>` - 与策略关联的对象池实例
- **Type Parameters**:
  - `T`: 池中对象的类型

### remove

> 移除与特定策略关联的对象池。

- **Parameters**:
  - `policy` (`ObjectPoolPolicy<?>`): 对象池策略
