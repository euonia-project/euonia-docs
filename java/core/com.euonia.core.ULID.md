# ULID

> ULID（Universally Unique Lexicographically Sortable Identifier，通用唯一字典序可排序标识符）生成器。ULID 是一个 128 位的通用唯一标识符，具有字典序可排序和 URL 安全的特性。

- **Type**: class
- **Package**: `com.euonia.core`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `CROCKFORD_BASE32` | `String` | Crockford Base32 编码字符集，排除了 I、L、O 等易混淆字母 |
| `SECURE_RANDOM` | `SecureRandom` | 密码学安全的随机数生成器 |

## Methods

### generate

> 生成一个新的 ULID 字符串。

- **Returns**: `String` - 一个 32 字符的 ULID 字符串
