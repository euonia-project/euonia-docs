# RuleResult

> 表示规则执行的结果，包含规则是否通过、结果描述、严重级别以及所执行规则的名称。

- **Type**: class (final class)
- **Package**: `com.euonia.osba.rules`
- **Author**: damon(zhaorong@outlook.com)

## Constructors

### `RuleResult(String ruleName)`
> 构造一个成功的结果，仅包含规则名称。

**Parameters:**
- `ruleName` (`String`): 规则名称

### `RuleResult(String ruleName, String description, RuleSeverity severity)`
> 使用指定的规则名称、描述和严重级别构造结果。
> 若严重级别为 `null`，则默认为 `RuleSeverity.SUCCESS`；
> 若描述为 `null` 或空白，则 `isSuccess()` 返回 `true`。

**Parameters:**
- `ruleName` (`String`): 规则名称
- `description` (`String`): 结果描述
- `severity` (`RuleSeverity`): 严重级别

## Methods

### `isSuccess(): boolean`
> 判断规则执行是否成功。当没有失败描述（即描述为 `null` 或空白）时视为成功。

**Returns:** `boolean` — 若规则执行成功则返回 `true`，否则返回 `false`

### `getDescription(): String`
> 获取规则执行结果的描述信息。若规则执行成功，此值可能为 `null` 或空白；若失败，则包含失败描述。

**Returns:** `String` — 规则执行结果的描述信息

### `getSeverity(): RuleSeverity`
> 获取规则执行结果的严重级别。严重级别表示规则执行结果的重要程度或影响，如成功、警告或错误。

**Returns:** `RuleSeverity` — 规则执行结果的严重级别

### `getRuleName(): String`
> 获取执行产生此结果的规则名称。

**Returns:** `String` — 所执行规则的名称

### `getProperties(): List<PropertyInfo<?>>`
> 获取与此规则结果关联的属性列表（不可修改）。可用于标识哪些属性受规则执行影响。

**Returns:** `List<PropertyInfo<?>>` — 与此规则结果关联的属性列表

### `setProperties(List<PropertyInfo<?>> properties): void`
> 设置与此规则结果关联的属性列表。可用于标识哪些属性受规则执行影响。

**Parameters:**
- `properties` (`List<PropertyInfo<?>>`): 要设置的属性列表
