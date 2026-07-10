# DefaultObjectPool

> 通用对象池实现，管理类型为 T 的可重用对象池。该池使用 `ObjectPoolPolicy` 来定义对象的创建、验证和销毁行为。对象在首次获取时惰性创建 —— 当空闲池为空且使用中的对象数低于容量时，才会创建新对象。
>
> 当池耗尽时，支持多种超限行为：
> - `THROW_EXCEPTION` —— 抛出 RuntimeException
> - `RETURN_NULL` —— 返回 null
> - `CREATE_NEW` —— 在容量之外创建新实例
> - `WAIT_FOR_AVAILABLE` —— 阻塞调用线程直到有对象被释放

- **Module**: `core`
- **Type**: `final class`
- **Package**: `com.euonia.core`
- **Implements**: [`ObjectPool`](./com.euonia.core.ObjectPool.md)&lt;T&gt;
- **Author**: damon(zhaorong@outlook.com)

## Type Parameters

| Parameter | Bound | Description |
|-----------|-------|-------------|
| `T` | *(无)* | 池管理的对象类型 |

## Methods

### DefaultObjectPool (constructor)

> 使用给定的策略和容量构造一个 DefaultObjectPool。

- **Parameters**:
  - `policy` (`ObjectPoolPolicy<T>`): 定义创建/验证/销毁/超限行为的策略
  - `capacity` (`int`): 触发超限行为之前允许的最大使用中对象数

### DefaultObjectPool (constructor)

> 使用给定的策略和默认容量 `Runtime.getRuntime().availableProcessors() * 2` 构造一个 DefaultObjectPool。

- **Parameters**:
  - `policy` (`ObjectPoolPolicy<T>`): 定义创建/验证/销毁/超限行为的策略

### getCapacity

> 返回此池的最大容量。

- **Returns**: `int` - 池容量

### getIdleCount

> 返回池中当前空闲（可用）对象的数量。

- **Returns**: `int` - 空闲对象计数

### getInUseCount

> 返回当前正在使用中（已获取但尚未释放）的对象数量。

- **Returns**: `int` - 使用中对象计数

### getPolicy

> 返回此池使用的策略。

- **Returns**: `ObjectPoolPolicy<T>` - 对象池策略

### release

> 将对象释放回池中。如果空闲池已满，该对象将通过策略被销毁。使用中计数器始终会递减。如果有任何线程处于 WAIT_FOR_AVAILABLE 模式等待，其中一个将被通知。

- **Parameters**:
  - `obj` (`T`): 要释放的对象；如果为 null，此方法为空操作

### acquire

> 从池中获取一个对象。正常路径（inUseCount < capacity）：如果空闲池中有可用对象，对其进行验证并返回；如果空闲池为空，通过策略创建新对象。超限路径（inUseCount >= capacity）：根据 oversizeBehavior 处理 —— THROW_EXCEPTION 抛出异常，RETURN_NULL 返回 null，CREATE_NEW 在容量之外创建新实例，WAIT_FOR_AVAILABLE 阻塞直到有对象被释放。

- **Returns**: `T` - 获取到的对象，如果超限行为为 RETURN_NULL 则返回 null
