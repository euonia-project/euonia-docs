# Resource

> 国际化资源文件读取工具类，提供从资源文件中获取字符串值的静态方法，并支持参数格式化。使用 `StackWalker` 自动检测调用者类以定位 `ClassLoader`。

- **Module**: `core`
- **Type**: `class`
- **Package**: `com.euonia.utility`
- **Author**: damon(zhaorong@outlook.com)

## Static Methods

### getString

> 获取指定资源文件中指定键的字符串值，并根据提供的参数进行格式化。使用默认区域设置。

- **Parameters**:
  - `baseName` (`String`): 资源文件的基本名称（不包含扩展名和路径）
  - `key` (`String`): 资源文件中对应的键
  - `args` (`Object...`): 可选的参数，用于 `String.format` 格式化字符串
- **Returns**: `String` - 格式化后的字符串值

### getString

> 获取指定资源文件中指定键的字符串值，使用指定的区域设置和参数进行格式化。

- **Parameters**:
  - `baseName` (`String`): 资源文件的基本名称（不包含扩展名和路径）
  - `key` (`String`): 资源文件中对应的键
  - `locale` (`Locale`): 指定的区域设置
  - `args` (`Object...`): 可选的参数，用于 `String.format` 格式化字符串
- **Returns**: `String` - 格式化后的字符串值

## Resource Bundles

Core 模块内置以下资源文件：

| 文件 | 用途 |
|------|------|
| `core.properties` | 默认（英文）消息 |
| `core_zh_HANS.properties` | 简体中文 |
| `core_zh_HANT.properties` | 繁体中文 |
| `reflection.properties` | 默认（英文）反射消息 |
| `reflection_zh_Hans.properties` | 简体中文反射消息 |
| `reflection_zh_Hant.properties` | 繁体中文反射消息 |

## Usage

```java
// 获取国际化消息
String msg = Resource.getString("core", "ArgumentNullException.Message1", "userId");
// → "参数 'userId' 不能为 null。"
```
