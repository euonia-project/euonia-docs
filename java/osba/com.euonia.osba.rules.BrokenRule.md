# BrokenRule

> 表示在规则检查过程中被违反的已破坏规则。包含有关违反规则的属性、违规描述以及严重程度的信息。

- **Type**: record
- **Package**: `com.euonia.osba.rules`
- **Author**: damon(zhaorong@outlook.com)

## Record Components

| Component | Type | Description |
|-----------|------|-------------|
| `property` | `String` | 违反规则的属性名称 |
| `description` | `String` | 违反规则的描述，提供有关违规的详细信息 |
| `severity` | `RuleSeverity` | 违反规则的严重程度，指示违规的严重性级别 |
