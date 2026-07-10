# ShortUniqueId

> ShortUniqueId 是一个工具类，用于从整数或长整数生成短且唯一的字符串 ID。
> 它提供了将整数、长整数和十六进制字符串编码为短唯一 ID 以及反向解码的方法。
> 该实现基于 Hashids 算法，该算法旨在创建短小、非连续且 URL 友好的 ID。

- **Module**: `core`
- **Type**: `final class`
- **Package**: `com.euonia.core`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### getDefault

> 获取默认的 ShortUniqueId 实例，使用默认的字母表、分隔符和盐值。

- **Returns**: `ShortUniqueId` - 默认的 ShortUniqueId 实例

### ShortUniqueId (constructor)

> 创建一个 ShortUniqueId 实例，使用默认的字母表、分隔符和盐值。

### ShortUniqueId (constructor)

> 创建一个 ShortUniqueId 实例，允许自定义盐值、最小哈希长度、字母表和分隔符。

- **Parameters**:
  - `salt` (`String`): 自定义盐值
  - `minHashLength` (`int`): 最小哈希长度
  - `alphabet` (`String`): 自定义字母表
  - `seps` (`String`): 自定义分隔符

### encode

> 将单个整数编码为短唯一字符串 ID。

- **Parameters**:
  - `number` (`int`): 要编码的整数
- **Returns**: `String` - 表示输入整数的短唯一字符串 ID

### encode

> 将一个或多个整数编码为短唯一字符串 ID。

- **Parameters**:
  - `numbers` (`int...`): 要编码的整数
- **Returns**: `String` - 表示输入整数的短唯一字符串 ID

### encode

> 将整数集合编码为短唯一字符串 ID。

- **Parameters**:
  - `numbers` (`Collection<Integer>`): 要编码的整数集合
- **Returns**: `String` - 表示输入整数的短唯一字符串 ID

### encode

> 将单个长整数编码为短唯一字符串 ID。

- **Parameters**:
  - `number` (`long`): 要编码的长整数
- **Returns**: `String` - 表示输入长整数的短唯一字符串 ID

### encode

> 将一个或多个长整数编码为短唯一字符串 ID。

- **Parameters**:
  - `numbers` (`long...`): 要编码的长整数
- **Returns**: `String` - 表示输入长整数的短唯一字符串 ID

### encode

> 将长整数集合编码为短唯一字符串 ID。

- **Parameters**:
  - `numbers` (`Collection<Long>`): 要编码的长整数集合
- **Returns**: `String` - 表示输入长整数的短唯一字符串 ID

### decode

> 将短唯一字符串 ID 解码回原始整数。

- **Parameters**:
  - `hash` (`String`): 要解码的短唯一字符串 ID
- **Returns**: `int[]` - 表示原始值的整数数组

### decodeLong

> 将短唯一字符串 ID 解码回原始长整数。

- **Parameters**:
  - `hash` (`String`): 要解码的短唯一字符串 ID
- **Returns**: `long[]` - 表示原始值的长整数数组

### encodeHex

> 将十六进制字符串编码为短唯一字符串 ID。输入的十六进制字符串被分割为每 12 个字符一块，每块前缀添加 '1' 以确保其可以被解析为有效的长整数。

- **Parameters**:
  - `hex` (`String`): 要编码的十六进制字符串
- **Returns**: `String` - 表示输入十六进制字符串的短唯一字符串 ID，如果输入无效则返回空字符串

### decodeHex

> 将短唯一字符串 ID 解码回原始十六进制字符串。

- **Parameters**:
  - `hash` (`String`): 要解码的短唯一字符串 ID
- **Returns**: `String` - 输入 ID 所表示的原始十六进制字符串，如果输入无效则返回空字符串

## Usage

```java
ShortUniqueId suid = ShortUniqueId.getDefault();

// 编码
String id = suid.encode(12345);
String ids = suid.encode(1, 2, 3);

// 解码
int[] numbers = suid.decode(id);

// 十六进制
String hex = suid.encodeHex("ABCDEF123456");
String original = suid.decodeHex(hex);
```
