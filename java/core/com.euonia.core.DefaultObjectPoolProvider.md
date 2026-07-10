# DefaultObjectPoolProvider

> 对象池提供者，用于根据提供的策略创建和管理对象池。
> 它使用并发映射来缓存不同策略的对象池，确保每个策略只有一个关联的池。

- **Module**: `core`
- **Type**: `final class`
- **Package**: `com.euonia.core`
- **Implements**: [`ObjectPoolProvider`](./com.euonia.core.ObjectPoolProvider.md)
- **Author**: damon(zhaorong@outlook.com)

## Methods

### getInstance

> 获取 DefaultObjectPoolProvider 的单例实例。

- **Returns**: `DefaultObjectPoolProvider` - 单例实例

### create

> 使用默认容量创建或获取与给定策略关联的 DefaultObjectPool。如果该策略的池已存在，则返回缓存的实例。

- **Parameters**:
  - `policy` (`ObjectPoolPolicy<T>`): 对象池策略
- **Returns**: `ObjectPool<T>` - 与策略关联的对象池

### create

> 使用指定容量创建或获取与给定策略关联的 DefaultObjectPool。如果该策略的池已存在，则返回缓存的实例。

- **Parameters**:
  - `policy` (`ObjectPoolPolicy<T>`): 对象池策略
  - `size` (`int`): 池容量
- **Returns**: `ObjectPool<T>` - 与策略关联的对象池

### remove

> 从缓存中移除与给定策略关联的对象池。

- **Parameters**:
  - `policy` (`ObjectPoolPolicy<?>`): 要移除其关联池的策略
