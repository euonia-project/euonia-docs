# Generic

> 抽象泛型工具类，用于在运行时解析泛型参数的实际类型。
>
> 通过匿名子类捕获泛型类型参数（"钻石"语法），然后扫描类层次结构中的类型变量到实际类型的映射关系，最终解析出具体的泛型类型。

- **Module**: `core`
- **Type**: `abstract class`
- **Package**: `com.euonia.reflection`
- **Author**: damon(zhaorong@outlook.com)

## Type Parameters

| Parameter | Bound | Description |
|-----------|-------|-------------|
| `C` | *(无)* | 要解析的泛型类型 |

## Methods

### Generic (constructor)

> 使用指定的上下文类构造 Generic 实例，并捕获泛型参数。

- **Parameters**:
  - `context` (`Class<?>`): 上下文类

### forType

> 为指定类型创建静态的 Generic 实例。

- **Parameters**:
  - `type` (`Class<T>`): 类型的 Class
- **Returns**: `Generic<T>` - 新的 Generic 实例
- **Type Parameters**:
  - `T`: 要解析的类型

### resolve

> 解析泛型参数的实际类型，结果会被缓存。

- **Returns**: `Class<? super C>` - 解析后的具体类

### setCache

> 设置泛型解析缓存，用于测试或自定义缓存策略。

- **Parameters**:
  - `cache` (`ConcurrentHashMap<Generic<?>, Type>`): 新的缓存映射

## Usage

```java
// 为指定类型创建 Generic 实例
Generic<MyService> generic = Generic.forType(MyService.class);

// 解析泛型参数的实际类型
Class<? super MyService> resolved = generic.resolve();
```
