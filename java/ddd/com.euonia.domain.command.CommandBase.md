# CommandBase

> 命令基类，实现 {@link Command} 接口并提供键值对属性存储功能。命令的属性以字符串形式存储，支持通过 {@link #get(String, Class)} 方法进行类型安全的属性值转换。具体的命令类应继承此基类。

- **Type**: abstract class
- **Package**: `com.euonia.domain.command`
- **Author**: damon(zhaorong@outlook.com)
- **Implements**: `Command`

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `properties` | `Map<String, String>` | 命令属性存储 |

## Methods

### getProperties

> 获取所有命令属性。

- **Returns**: `Map<String, String>` - 属性映射

### get

> 根据键获取属性值，如果键不存在则返回 null。

- **Parameters**:
  - `property` (`String`): 属性键
- **Returns**: `String` - 属性值，如果键不存在则返回 null

### set

> 设置属性键值对。

- **Parameters**:
  - `property` (`String`): 属性键
  - `value` (`String`): 属性值

### get

> 根据键获取属性值，并强制转换为指定类型。使用 {@link TypeHelper#coerceValue} 进行类型转换。

- **Parameters**:
  - `property` (`String`): 属性键
  - `castType` (`Class<T>`): 目标类型
- **Returns**: `T` - 强制转换后的属性值，如果键不存在则返回 null
