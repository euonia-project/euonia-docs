# BrokenRuleCollection

> 表示在规则检查过程中被违反的已破坏规则的集合。提供管理已破坏规则集合的方法，包括添加新的已破坏规则、清除现有规则以及根据严重程度检索已破坏规则的数量。

- **Type**: class
- **Package**: `com.euonia.osba.rules`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### clearRules

> 清除集合中的所有已破坏规则，无论其关联的属性如何。

### clearRules

> 清除集合中与指定属性名称关联的已破坏规则。

- **Parameters**:
  - `propertyName` (`String`): 应清除其关联已破坏规则的属性名称

### add

> 根据提供的规则结果列表和关联的属性名称，向集合中添加新的已破坏规则。

- **Parameters**:
  - `results` (`List<RuleResult>`): 要添加为已破坏规则的规则结果列表
  - `propertyName` (`String`): 与已破坏规则关联的属性名称

### getErrorCount

> 检索集合中严重级别为 ERROR 的已破坏规则数量。

- **Returns**: `int` — 严重级别为 ERROR 的已破坏规则数量

### getWarningCount

> 检索集合中严重级别为 WARNING 的已破坏规则数量。

- **Returns**: `int` — 严重级别为 WARNING 的已破坏规则数量

### getInformationCount

> 检索集合中严重级别为 INFORMATION 的已破坏规则数量。

- **Returns**: `int` — 严重级别为 INFORMATION 的已破坏规则数量

### isEmpty

> 检查已破坏规则集合是否为空。

- **Returns**: `boolean` — 如果集合为空则返回 true，否则返回 false

### list

> 返回集合中已破坏规则的不可修改列表。

- **Returns**: `List<BrokenRule>` — 已破坏规则的不可修改列表

### stream

> 返回集合中已破坏规则的流。

- **Returns**: `Stream<BrokenRule>` — 已破坏规则的流
