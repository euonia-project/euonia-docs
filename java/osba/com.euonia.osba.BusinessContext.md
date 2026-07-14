# BusinessContext

> 业务上下文，为 OSBA 工厂创建的业务对象提供轻量级的服务解析和实例创建网关。

- **Type**: final class
- **Package**: `com.euonia.osba`
- **Author**: damon(zhaorong@outlook.com)

## Constructors

### `BusinessContext(Function<Class<?>, ?> instanceCreator, ObjectFactory objectFactory)`

> 使用指定的实例创建函数和 ObjectFactory 创建 BusinessContext 的新实例。

**Parameters:**
- `instanceCreator` (`Function<Class<?>, ?>`): 用于创建指定类型实例的函数
- `objectFactory` (`ObjectFactory`): 此 BusinessContext 使用的 ObjectFactory

## Methods

### `<T> getOrCreateObject(Class<T> objectType): T`

> 从上下文中获取指定类型的实例，如果不存在则创建。

**Parameters:**
- `objectType` (`Class<T>`): 要获取或创建的对象的类型

**Returns:** `T` — 指定类型的实例

**Throws:** `NullPointerException` — 当 objectType 为 null 时抛出
**Throws:** `IllegalStateException` — 当 instanceCreator 为 null 时抛出

### `getObjectFactory(): ObjectFactory`

> 获取与此 BusinessContext 关联的 ObjectFactory，该工厂可用于基于注解的工厂方法创建、获取、插入、更新、保存、执行和删除业务对象。

**Returns:** `ObjectFactory` — 与此 BusinessContext 关联的 ObjectFactory
