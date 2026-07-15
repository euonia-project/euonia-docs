# ArgumentOutOfRangeException

> 参数超出范围异常类，提供静态守卫方法用于检查方法参数是否在合法范围内。支持比较、区间和数值符号检查。继承自 `IllegalArgumentException`。

- **Module**: `core`
- **Type**: `class`
- **Package**: `com.euonia.core`
- **Extends**: `IllegalArgumentException`
- **Author**: damon(zhaorong@outlook.com)

## Constructors

### ArgumentOutOfRangeException

> 使用指定的详细消息构造异常。

- **Parameters**:
  - `message` (`String`): 异常的详细消息

## Static Methods

### throwIfEquals

> 检查参数是否等于目标值，如果是则抛出异常。

- **Type Parameters**:
  - `T extends Comparable<T>`: 参数类型
- **Parameters**:
  - `argument` (`T`): 要检查的参数
  - `target` (`T`): 目标值
  - `param` (`String`): 参数名称
- **Throws**: `ArgumentOutOfRangeException` - 如果 argument 等于 target

### throwIfGreaterThan

> 检查参数是否大于目标值，如果是则抛出异常。

- **Type Parameters**:
  - `T extends Comparable<T>`: 参数类型
- **Parameters**:
  - `argument` (`T`): 要检查的参数
  - `target` (`T`): 目标值
  - `param` (`String`): 参数名称
- **Throws**: `ArgumentOutOfRangeException` - 如果 argument > target

### throwIfGreaterThanOrEqual

> 检查参数是否大于或等于目标值，如果是则抛出异常。

- **Type Parameters**:
  - `T extends Comparable<T>`: 参数类型
- **Parameters**:
  - `argument` (`T`): 要检查的参数
  - `target` (`T`): 目标值
  - `param` (`String`): 参数名称
- **Throws**: `ArgumentOutOfRangeException` - 如果 argument >= target

### throwIfLessThan

> 检查参数是否小于目标值，如果是则抛出异常。

- **Type Parameters**:
  - `T extends Comparable<T>`: 参数类型
- **Parameters**:
  - `argument` (`T`): 要检查的参数
  - `target` (`T`): 目标值
  - `param` (`String`): 参数名称
- **Throws**: `ArgumentOutOfRangeException` - 如果 argument < target

### throwIfLessThanOrEqual

> 检查参数是否小于或等于目标值，如果是则抛出异常。

- **Type Parameters**:
  - `T extends Comparable<T>`: 参数类型
- **Parameters**:
  - `argument` (`T`): 要检查的参数
  - `target` (`T`): 目标值
  - `param` (`String`): 参数名称
- **Throws**: `ArgumentOutOfRangeException` - 如果 argument <= target

### throwIfNotInRange

> 检查参数是否不在 [min, max] 区间内，如果是则抛出异常。

- **Type Parameters**:
  - `T extends Comparable<T>`: 参数类型
- **Parameters**:
  - `argument` (`T`): 要检查的参数
  - `min` (`T`): 范围最小值
  - `max` (`T`): 范围最大值
  - `param` (`String`): 参数名称
- **Throws**: `ArgumentOutOfRangeException` - 如果 argument < min 或 argument > max

### throwIfNotInRange

> 检查参数是否不在 Range 区间内，如果是则抛出异常。

- **Type Parameters**:
  - `T extends Comparable<T>`: 参数类型
- **Parameters**:
  - `argument` (`T`): 要检查的参数
  - `range` (`Range<T>`): 范围对象
  - `param` (`String`): 参数名称
- **Throws**: `ArgumentOutOfRangeException` - 如果 argument 不在范围内

### throwIfInRange

> 检查参数是否在 [min, max] 区间内，如果是则抛出异常。

- **Type Parameters**:
  - `T extends Comparable<T>`: 参数类型
- **Parameters**:
  - `argument` (`T`): 要检查的参数
  - `min` (`T`): 范围最小值
  - `max` (`T`): 范围最大值
  - `param` (`String`): 参数名称
- **Throws**: `ArgumentOutOfRangeException` - 如果 min <= argument <= max

### throwIfNegative

> 检查数值是否为负数，如果是则抛出异常。

- **Parameters**:
  - `argument` (`Number`): 要检查的数值
  - `param` (`String`): 参数名称
- **Throws**: `ArgumentOutOfRangeException` - 如果 argument < 0

### throwIfNegativeOrZero

> 检查数值是否为负数或零，如果是则抛出异常。

- **Parameters**:
  - `argument` (`Number`): 要检查的数值
  - `param` (`String`): 参数名称
- **Throws**: `ArgumentOutOfRangeException` - 如果 argument <= 0

### throwIfZero

> 检查数值是否为零，如果是则抛出异常。

- **Parameters**:
  - `argument` (`Number`): 要检查的数值
  - `param` (`String`): 参数名称
- **Throws**: `ArgumentOutOfRangeException` - 如果 argument == 0

## Usage

```java
// 比较检查
ArgumentOutOfRangeException.throwIfGreaterThan(age, 150, "age");
ArgumentOutOfRangeException.throwIfLessThan(age, 0, "age");

// 区间检查
ArgumentOutOfRangeException.throwIfNotInRange(score, 0, 100, "score");

// 使用 Range 对象
Range<Integer> validRange = Range.of(0, 100);
ArgumentOutOfRangeException.throwIfNotInRange(score, validRange, "score");

// 数值符号检查
ArgumentOutOfRangeException.throwIfNegative(price, "price");
ArgumentOutOfRangeException.throwIfZero(count, "count");
```
