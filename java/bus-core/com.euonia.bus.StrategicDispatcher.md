# StrategicDispatcher
> 基于已配置的策略和约定为消息类型确定传输的分发器。它使用缓存来存储消息类型的传输判定结果以提高性能。
- **Type**: class
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `transportCache` | `ConcurrentHashMap<String, List<String>>` | 传输判定结果缓存 |
| `configurator` | `Configurator` | 消息总线配置器 |

## Methods
### StrategicDispatcher
> 使用指定的配置器创建 `StrategicDispatcher` 的新实例。
- **Parameters**:
  - `configurator` (`Configurator`): 消息总线配置器

### determine
> 为指定的消息类型创建传输列表。
- **Parameters**:
  - `channel` (`String`): 通道名称
  - `messageType` (`Class<?>`): 消息的类型
- **Returns**: `List<String>` - 消息应被分发到的传输名称列表
