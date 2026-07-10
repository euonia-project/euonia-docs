# ServiceProvider

> ServiceProvider 是一个接口，定义了用于解析和创建服务实例的方法。此接口的实现可以提供自定义逻辑来检索和实例化服务。

- **Module**: `core`
- **Type**: `interface`
- **Package**: `com.euonia.reflection`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### getService

> 检索指定类型的服务实例。

- **Parameters**:
  - `type` (`Class<T>`): 服务的类
- **Returns**: `Optional<T>` - 包含服务实例的 Optional，如果未找到则为空

### getService

> 检索指定类型和泛型类型参数的服务实例。

- **Parameters**:
  - `type` (`Class<T>`): 服务的类
  - `genericTypeArguments` (`Class<?>...`): 服务的泛型类型参数
- **Returns**: `Optional<T>` - 包含服务实例的 Optional，如果未找到则为空

### getService

> 检索指定类型和服务名称的服务实例。

- **Parameters**:
  - `type` (`Class<T>`): 服务的类
  - `serviceName` (`String`): 服务名称
- **Returns**: `Optional<T>` - 包含服务实例的 Optional，如果未找到则为空

### getRequiredService

> 获取指定类型的服务实例，如果未找到则抛出异常。

- **Parameters**:
  - `type` (`Class<T>`): 服务的类
- **Returns**: `T` - 服务实例
- **Throws**: `IllegalStateException` - 如果服务未找到

### getServices

> 获取指定类型的所有服务实例。

- **Parameters**:
  - `type` (`Class<T>`): 服务的类
- **Returns**: `List<T>` - 服务实例列表

### getServices

> 获取指定类型和泛型类型参数的所有服务实例。

- **Parameters**:
  - `type` (`Class<T>`): 服务的类
  - `genericTypeArguments` (`Class<?>...`): 服务的泛型类型参数
- **Returns**: `List<T>` - 服务实例列表

### createInstance

> 使用指定的构造函数参数创建类型的新实例。

- **Parameters**:
  - `type` (`Class<T>`): 要实例化的类型
  - `constructorArguments` (`Object...`): 构造函数参数
- **Returns**: `T` - 新创建的实例
