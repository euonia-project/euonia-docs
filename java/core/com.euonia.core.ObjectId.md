# ObjectId

> ObjectId 是一个表示对象唯一标识符的类。可以使用不同的算法生成，如 Snowflake、GUID、Random 和 ULID。ObjectId 的值可以是 long、String、UUID 或 Integer 类型。该类提供了使用不同算法生成 ObjectId 的方法，并重写了 hashCode、equals 和 toString 方法以确保正确的功能。ObjectId 类是不可变的，这意味着一旦创建，其值就不能更改。

- **Module**: `core`
- **Type**: `final class`
- **Package**: `com.euonia.core`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### getValue

> 获取 ObjectId 的值。

- **Returns**: `Object` - ObjectId 的值

### ObjectId (constructor)

> 使用指定的值构造 ObjectId。

- **Parameters**:
  - `value` (`long`): ObjectId 的值

### ObjectId (constructor)

> 使用指定的值构造 ObjectId。

- **Parameters**:
  - `value` (`String`): ObjectId 的值

### ObjectId (constructor)

> 使用指定的值构造 ObjectId。

- **Parameters**:
  - `value` (`UUID`): ObjectId 的值

### ObjectId (constructor)

> 使用指定的值构造 ObjectId。

- **Parameters**:
  - `value` (`Integer`): ObjectId 的值

### snowflake

> 使用 Snowflake 算法生成新的 ObjectId。

- **Returns**: `ObjectId` - 新的 ObjectId

### guid

> 使用 GUID 算法生成新的 ObjectId（默认类型）。

- **Returns**: `ObjectId` - 新的 ObjectId

### guid

> 使用 GUID 算法生成新的 ObjectId。

- **Parameters**:
  - `type` (`GuidType`): GUID 生成策略
- **Returns**: `ObjectId` - 新的 ObjectId

### random

> 使用 Random 算法生成新的 ObjectId。

- **Returns**: `ObjectId` - 新的 ObjectId

### ulid

> 使用 ULID 算法生成新的 ObjectId。

- **Returns**: `ObjectId` - 新的 ObjectId

### newRandomId

> 生成新的随机字符串 ID。

- **Parameters**:
  - `seed` (`long`): 种子值
- **Returns**: `String` - 新的随机字符串 ID

## Usage

```java
// 使用不同算法生成 ObjectId
ObjectId id1 = ObjectId.snowflake();
ObjectId id2 = ObjectId.guid();
ObjectId id3 = ObjectId.guid(GuidType.SEQUENTIAL_AS_STRING);
ObjectId id4 = ObjectId.random();
ObjectId id5 = ObjectId.ulid();

// 生成随机字符串 ID
String randomId = ObjectId.newRandomId(System.currentTimeMillis());
```

- **Parameters**:
  - `seed` (`long`): 种子值
- **Returns**: `String` - 新的随机字符串 ID

### newRandomId

> 使用当前时间作为种子生成新的随机字符串 ID。

- **Returns**: `String` - 新的随机字符串 ID

### newSnowflakeId

> 生成新的 Snowflake ID。

- **Returns**: `long` - 新的 Snowflake ID

### newGuid

> 使用默认生成策略生成新的 GUID。

- **Returns**: `UUID` - 新的 GUID

### newGuid

> 根据指定的类型生成新的 GUID。

- **Parameters**:
  - `type` (`GuidType`): GUID 生成策略
- **Returns**: `UUID` - 新的 GUID

### newUlid

> 生成新的 ULID 字符串。

- **Returns**: `String` - 新的 ULID 字符串

### getValue

> 获取 ObjectId 的值。

- **Returns**: `Object` - ObjectId 的值

### getValue

> 获取指定类型的 ObjectId 值。

- **Parameters**:
  - `type` (`Class<T>`): 期望的类型
- **Returns**: `T` - 转换后的值，如果不匹配则返回 null

### hashCode

> 返回值的哈希码。

- **Returns**: `int` - 哈希码

### equals

> 比较两个 ObjectId 是否相等。

- **Parameters**:
  - `obj` (`Object`): 要比较的对象
- **Returns**: `boolean` - 相等返回 true

### toString

> 返回值的字符串表示。

- **Returns**: `String` - 字符串表示
