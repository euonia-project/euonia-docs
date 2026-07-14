# Rules

> 规则管理器，负责管理业务对象的验证规则执行，跟踪已违反的规则并在验证完成时通知监听器。

- **Type**: class (final class)
- **Package**: `com.euonia.osba.rules`
- **Author**: damon(zhaorong@outlook.com)

## Constructors

### `Rules(RuleCheckable target)`
> 构造方法，创建指定目标对象的规则管理器。

**Parameters:**
- `target` (`RuleCheckable`): 待验证的目标对象

## Methods

### `getRuleManager(): RuleManager`
> 获取目标对象的规则管理器，必要时进行初始化。

**Returns:** `RuleManager` — 目标对象对应的规则管理器

### `addRule(Rule rule): void`
> 向目标对象的规则管理器中添加验证规则。

**Parameters:**
- `rule` (`Rule`): 要添加的验证规则

### `getBrokenRules(): BrokenRuleCollection`
> 获取规则检查过程中已识别的违反规则集合。

**Returns:** `BrokenRuleCollection` — 已违反规则的集合

### `isValid(): boolean`
> 基于当前的已违反规则集合判断目标对象是否有效。

**Returns:** `boolean` — 若目标对象有效返回 true，否则返回 false

### `hasRunningRules(): boolean`
> 检查当前是否有正在为目标对象运行的规则。

**Returns:** `boolean` — 若有规则正在运行返回 true，否则返回 false

### `isSuppressRuleChecking(): boolean`
> 获取目标对象的规则检查当前是否被抑制。当规则检查被抑制时，不会执行任何规则，对象将被视为有效。

**Returns:** `boolean` — 若规则检查被抑制返回 true，否则返回 false

### `setSuppressRuleChecking(boolean suppressRuleChecking): void`
> 设置目标对象的规则检查当前是否被抑制。当规则检查被抑制时，不会执行任何规则，对象将被视为有效。

**Parameters:**
- `suppressRuleChecking` (`boolean`): true 表示抑制规则检查，false 表示启用规则检查

### `addValidationCompleteListener(Consumer<BrokenRuleCollection> listener): void`
> 添加验证完成时的通知监听器。监听器将接收已违反规则的集合作为参数。

**Parameters:**
- `listener` (`Consumer<BrokenRuleCollection>`): 要添加的监听器

### `removeValidationCompleteListener(Consumer<BrokenRuleCollection> listener): void`
> 移除验证完成时的通知监听器。

**Parameters:**
- `listener` (`Consumer<BrokenRuleCollection>`): 要移除的监听器

### `checkObjectRules(): List<String>`
> 检查目标对象的所有验证规则，并相应更新已违反规则的集合。该方法返回受影响的属性名称列表。

**Returns:** `List<String>` — 受影响的属性名称列表

### `addDataAnnotationRules(): void`
> 扫描目标对象上的数据注解并向规则管理器添加对应的 DataAnnotationRule。
