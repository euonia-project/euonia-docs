# Singleton

> Singleton 是一个线程安全的单例工厂类，用于管理和提供全局唯一的实例。它使用 ConcurrentHashMap 来存储不同类型的实例，并通过 computeIfAbsent 方法确保每个类型只有一个实例被创建。

- **Type**: class
- **Package**: `com.euonia.core`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `instances` | `ConcurrentHashMap<Class<?>, Object>` | 存储不同类型的实例 |

## Methods

### getInstance

> 获取指定类型的单例实例。如果实例不存在，则使用反射创建一个新的实例。

- **Parameters**:
  - `clazz` (`Class<T>`): 要获取实例的类对象
- **Returns**: `T` - 指定类型的单例实例

### get

> 获取指定类型的单例实例。如果实例不存在，则使用提供的 Supplier 创建一个新的实例。

- **Parameters**:
  - `clazz` (`Class<T>`): 要获取实例的类对象
  - `supplier` (`Supplier<T>`): 用于创建实例的 Supplier
- **Returns**: `T` - 指定类型的单例实例
