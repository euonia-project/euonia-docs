# RuleManager

> 管理与特定类型关联的规则，提供获取和管理该类型规则的方法。
>
> RuleManager 设计为线程安全，允许并发访问和修改规则而无需外部同步。
> 内部使用 `ConcurrentMap` 存储不同类型对应的 RuleManager 实例，
> 使用 `CopyOnWriteArrayList` 存储每个类型的规则列表，确保修改规则时不影响并发读取。

- **Type**: class (final class)
- **Package**: `com.euonia.osba.rules`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### `getRules(): List<Rule>`
> 获取当前类型对应的规则列表。

**Returns:** `List<Rule>` — 规则列表

### `isInitialized(): boolean`
> 判断当前 RuleManager 是否已完成初始化。此属性可用于确定规则是否已设置完毕并准备就绪。

**Returns:** `boolean` — 若已初始化则返回 `true`，否则返回 `false`

### `setInitialized(boolean initialized): void`
> 设置当前 RuleManager 的初始化状态。可在为关联类型添加完规则后调用此方法将 RuleManager 标记为已初始化。

**Parameters:**
- `initialized` (`boolean`): `true` 表示已初始化，`false` 表示未初始化

## Static Methods

### `getRules(Class<?> type): RuleManager`
> 获取与指定类型关联的 RuleManager 实例。若该类型尚无对应的 RuleManager，则创建新实例并存入映射。

**Parameters:**
- `type` (`Class<?>`): 要获取其 RuleManager 的类类型

**Returns:** `RuleManager` — 与指定类型关联的 RuleManager 实例

### `cleanRules(Class<?> type): void`
> 移除与指定类型关联的 RuleManager，相当于清除该类型的所有规则。

**Parameters:**
- `type` (`Class<?>`): 要清除规则的类类型
