# RuleContext

> 规则执行上下文，承载规则执行过程中的目标对象、当前规则、属性名和结果列表。
>
> 规则执行完毕后，调用 `complete()` 方法触发完成回调，若结果列表为空则自动添加成功结果。

- **Type**: class
- **Package**: `com.euonia.osba.rules`
- **Author**: damon(zhaorong@outlook.com)

## Constructors

### `RuleContext(Consumer<RuleContext> completeAction)`
> 使用指定的完成回调构造上下文。

**Parameters:**
- `completeAction` (`Consumer<RuleContext>`): 规则执行完成后的回调操作

## Methods

### `getRule(): Rule`
> 获取当前正在执行的规则。

**Returns:** `Rule` — 当前规则

### `setRule(Rule rule): void`
> 设置当前正在执行的规则。

**Parameters:**
- `rule` (`Rule`): 要设置的规则

### `getTarget(): Object`
> 获取规则校验的目标对象。

**Returns:** `Object` — 目标对象

### `setTarget(Object target): void`
> 设置规则校验的目标对象。

**Parameters:**
- `target` (`Object`): 目标对象

### `getPropertyName(): String`
> 获取当前正在校验的属性名。

**Returns:** `String` — 属性名

### `setPropertyName(String propertyName): void`
> 设置当前正在校验的属性名。

**Parameters:**
- `propertyName` (`String`): 属性名

### `getResults(): List<RuleResult>`
> 获取规则执行的结果列表（不可修改）。

**Returns:** `List<RuleResult>` — 不可修改的结果列表

### `addErrorResult(String description): void`
> 添加一条严重级别为 `RuleSeverity.ERROR` 的错误结果。

**Parameters:**
- `description` (`String`): 错误描述

### `addWarningResult(String description): void`
> 添加一条严重级别为 `RuleSeverity.WARNING` 的警告结果。

**Parameters:**
- `description` (`String`): 警告描述

### `addInformationResult(String description): void`
> 添加一条严重级别为 `RuleSeverity.INFORMATION` 的信息结果。

**Parameters:**
- `description` (`String`): 信息描述

### `addSuccessResult(): void`
> 添加一条成功结果（无严重级别）。

### `complete(): void`
> 完成规则执行，若结果列表为空则自动添加成功结果，然后触发完成回调。
