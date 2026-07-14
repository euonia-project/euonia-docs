# RuleCheckable

> 表示实现类具有规则检查功能。

- **Type**: interface
- **Package**: `com.euonia.osba.abstracts`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### isValid(): boolean

> 根据当前已破坏的规则指示对象是否有效。

**Returns:** `boolean` — 如果对象有效则返回 true，否则返回 false

### ruleCheckComplete(PropertyInfo<?> property): void

> 指示对象的规则检查已完成，并且已破坏的规则集合已更新以反映当前状态。

**Parameters:**
- `property` (`PropertyInfo<?>`): 已完成规则检查的属性

### ruleCheckComplete(String propertyName): void

> 指示对象的规则检查已完成，并且已破坏的规则集合已更新以反映当前状态。

**Parameters:**
- `propertyName` (`String`): 已完成规则检查的属性名称

### allRulesComplete(): void

> 指示对象的规则检查已完成，并且已破坏的规则集合已更新以反映当前状态。

### suspendRuleChecking(): void

> 暂停对象的规则检查。当规则检查被暂停时，对属性的更改将不会触发规则评估或更新已破坏的规则集合。当需要对对象执行多次更新，并希望在所有更改完成之前避免中间规则检查时，此功能非常有用。

### resumeRuleChecking(): void

> 在暂停后恢复对象的规则检查。当规则检查恢复时，暂停期间对属性所做的任何更改都将触发规则评估，并且已破坏的规则集合将相应更新。这可以确保在规则检查暂停期间进行多次更改后，对象的有效性能够准确反映。

### getBrokenRules(): BrokenRuleCollection

> 获取对象的已破坏规则集合。

**Returns:** `BrokenRuleCollection` — 已破坏规则的集合
