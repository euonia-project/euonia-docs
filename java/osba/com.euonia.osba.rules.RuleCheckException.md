# RuleCheckException

> 规则校验异常，当对象不满足保存条件时抛出。
>
> 该异常携带按属性名分组的校验错误信息，并通过 `ResponseHttpStatusCode` 注解标记对应的 HTTP 状态码为 400（Bad Request）。

- **Type**: class
- **Package**: `com.euonia.osba.rules`
- **Author**: damon(zhaorong@outlook.com)
- **Extends**: `RuntimeException`

## Constructors

### `RuleCheckException(Map<String, List<String>> errors)`
> 使用指定的校验错误信息构造异常。

**Parameters:**
- `errors` (`Map<String, List<String>>`): 按属性名分组的校验错误映射，key 为属性名，value 为错误消息列表

## Methods

### `getErrors(): Map<String, List<String>>`
> 获取按属性名分组的校验错误信息。

**Returns:** `Map<String, List<String>>` — 不可修改的校验错误映射，key 为属性名，value 为错误消息列表
