# Range

> 泛型不可变范围记录类，定义最小值和最大值边界。类型参数必须实现 `Comparable` 接口，以便比较范围的边界。

- **Module**: `core`
- **Type**: `record`
- **Package**: `com.euonia.core`
- **Author**: damon(zhaorong@outlook.com)

## Type Parameters

| Parameter | Bound | Description |
|-----------|-------|-------------|
| `T` | `extends Comparable<T>` | 范围值的类型 |

## Record Components

| Component | Type | Description |
|-----------|------|-------------|
| `min` | `T` | 范围的最小值（含） |
| `max` | `T` | 范围的最大值（含） |

## Methods

### of

> 创建一个新的 Range 实例。最小值不能大于最大值，否则将抛出 IllegalArgumentException。

- **Type Parameters**:
  - `T extends Comparable<T>`: 范围值的类型
- **Parameters**:
  - `min` (`T`): 范围的最小值
  - `max` (`T`): 范围的最大值
- **Returns**: `Range<T>` - 新的 Range 实例
- **Throws**: `IllegalArgumentException` - 如果 min > max

### check

> 检查给定的值是否在范围内（闭区间）。如果 min <= value <= max，返回 true；否则返回 false。

- **Parameters**:
  - `value` (`T`): 要检查的值
- **Returns**: `boolean` - 值在范围内时返回 true

## Usage

```java
Range<Integer> validRange = Range.of(0, 100);
validRange.check(50);   // true
validRange.check(-1);   // false
validRange.check(150);  // false

// 配合 ArgumentOutOfRangeException 使用
ArgumentOutOfRangeException.throwIfNotInRange(score, validRange, "score");
```
