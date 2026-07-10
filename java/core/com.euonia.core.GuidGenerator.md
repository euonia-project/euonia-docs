# GuidGenerator

> 使用与框架 .NET GUID 生成模式相匹配的布局生成 UUID 值。

- **Type**: class
- **Package**: `com.euonia.core`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `DOTNET_EPOCH_OFFSET_MILLIS` | `long` | .NET 纪元偏移量（62,135,596,800,000L），用于时间戳转换 |
| `SECURE_RANDOM` | `SecureRandom` | 密码学安全的随机数生成器 |

## Methods

### generate

> 使用指定的 GUID 生成模式创建 UUID。

- **Parameters**:
  - `type` (`GuidType`): 请求的 GUID 类型
- **Returns**: `UUID` - 生成的 UUID
