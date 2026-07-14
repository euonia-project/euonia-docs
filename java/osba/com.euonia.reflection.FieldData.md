# FieldData

> 表示对象的一个字段，可以跟踪其变化。此类提供了获取和设置字段值的方法，以及将其标记为未更改或撤销更改的方法。

- **Type**: class
- **Package**: `com.euonia.reflection`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<T>` — 字段值的类型
- **Implements**: `TrackableObject`

## Constructors

### `FieldData()`
> 创建一个新的 FieldData 实例。

### `FieldData(String name)`
> 使用指定的名称创建一个新的 FieldData 实例。

**Parameters:**
- `name` (`String`): 字段的名称

## Methods

### `getName(): String`
> 获取字段的名称。

**Returns:** `String` — 字段的名称

### `getValue(): T`
> 获取字段的当前值。

**Returns:** `T` — 字段的当前值

### `setValue(T value): void`
> 设置字段的值，并将其添加到历史记录中。

**Parameters:**
- `value` (`T`): 要设置的新值

### `markAsUnchanged(): void`
> 将字段标记为未更改，清除历史记录。

### `undo(): void`
> 撤销字段的最后一次更改。

### `isChanged(): boolean`
> 检查字段是否已更改。

**Returns:** `boolean` — 如果字段已更改，则返回 true；否则返回 false

### `isDeleted(): boolean`
> 检查字段是否已删除。

**Returns:** `boolean` — 如果字段已删除，则返回 true；否则返回 false

### `isNew(): boolean`
> 检查字段是否为新创建的对象。

**Returns:** `boolean` — 如果字段为新创建的对象，则返回 true；否则返回 false

### `isSavable(): boolean`
> 检查字段是否可保存。

**Returns:** `boolean` — 如果字段可保存，则返回 true；否则返回 false

### `isValid(): boolean`
> 检查字段是否有效。

**Returns:** `boolean` — 如果字段有效，则返回 true；否则返回 false

### `isBusy(): boolean`
> 检查字段是否忙碌。

**Returns:** `boolean` — 如果字段忙碌，则返回 true；否则返回 false
