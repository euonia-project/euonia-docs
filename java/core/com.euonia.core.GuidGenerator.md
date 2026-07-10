# GuidGenerator

> 使用与框架 .NET GUID 生成模式相匹配的布局生成 UUID 值。

- **Module**: `core`
- **Type**: `final class`
- **Package**: `com.euonia.core`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### generate

> 使用指定的 GUID 生成模式创建 UUID。

- **Parameters**:
  - `type` (`GuidType`): 请求的 GUID 类型
- **Returns**: `UUID` - 生成的 UUID

## Usage

```java
UUID uuid = GuidGenerator.generate(GuidType.SEQUENTIAL_AS_STRING);
```
