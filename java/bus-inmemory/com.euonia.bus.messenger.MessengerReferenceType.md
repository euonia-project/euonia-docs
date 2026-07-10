# MessengerReferenceType

> 定义 `Messenger` 实现所使用的引用类型。这是 .NET `MessengerReferenceType` 枚举的 Java 等价物。

- **Type**: `enum`
- **Package**: `com.euonia.bus.messenger`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Name | Type | Modifiers | Description |
|------|------|-----------|-------------|

## Enum Constants

| Name | Description |
|------|-------------|
| `STRONG` | 使用强引用来跟踪已注册的接收者。接收者必须手动取消注册以避免内存泄漏。 |
| `WEAK` | 使用弱引用来跟踪已注册的接收者。不再被其他地方引用的接收者将被自动垃圾回收。 |
