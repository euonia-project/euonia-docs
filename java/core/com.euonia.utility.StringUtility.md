# StringUtility

> StringUtility 是一个工具类，提供字符串操作的常用方法。旨在简化字符串处理并提高代码可读性。

- **Module**: `core`
- **Type**: `final class`
- **Package**: `com.euonia.utility`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### isNullOrEmpty

> 检查给定的字符串是否为 null 或空字符串。

- **Parameters**:
  - `input` (`String`): 要检查的字符串
- **Returns**: `boolean` - 如果字符串为 null 或空字符串，则返回 true

### isNullOrBlank

> 检查给定的字符串是否为 null、空字符串或仅包含空白字符。

- **Parameters**:
  - `input` (`String`): 要检查的字符串
- **Returns**: `boolean` - 如果字符串为 null、空字符串或仅包含空白字符，则返回 true

### capitalizeFirstLetter

> 将输入字符串的首字母大写。

- **Parameters**:
  - `input` (`String`): 要处理的字符串
- **Returns**: `String` - 首字母大写后的字符串

### decapitalizeFirstLetter

> 将输入字符串的首字母小写。

- **Parameters**:
  - `input` (`String`): 要处理的字符串
- **Returns**: `String` - 首字母小写后的字符串

### capitalizeFirstLetterWithUnderscore

> 将输入字符串的首字母大写，并在单词之间添加下划线。

- **Parameters**:
  - `input` (`String`): 要处理的字符串
- **Returns**: `String` - 首字母大写并添加下划线后的字符串

### collapse

> 接受一个字符串数组，并返回第一个非空且非空字符串的值。如果所有字符串都是空的或 null，则返回 null。

- **Parameters**:
  - `parts` (`String...`): 要处理的字符串数组
- **Returns**: `String` - 第一个非空且非空字符串的值，如果全部为空或 null 则返回 null

### collapse

> 接受一个字符串供应者数组，并返回第一个非空且非空字符串的值。如果所有字符串都是空的或 null，则返回 null。

- **Parameters**:
  - `suppliers` (`Supplier<String>...`): 要处理的字符串供应者数组
- **Returns**: `String` - 第一个非空且非空字符串的值，如果全部为空或 null 则返回 null
