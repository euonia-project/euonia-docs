# Validator

> Validator 接口定义了一个通用的验证器，用于对注解和对应的值进行验证。实现该接口的类需要提供具体的验证逻辑。

- **Module**: `core`
- **Type**: `interface`
- **Package**: `com.euonia.annotation`
- **Author**: damon(zhaorong@outlook.com)

## Type Parameters

| Parameter | Bound | Description |
|-----------|-------|-------------|
| `A` | `extends Annotation` | 注解类型，必须是 Annotation 的子类 |

## Methods

### validate

> 验证给定的注解和对应的值是否符合验证规则。

- **Parameters**:
  - `annotation` (`A`): 要验证的注解实例
  - `value` (`Object`): 要验证的值
- **Returns**: [`Result`](#result) - 一个 Result 对象，其中 result 表示验证结果（true 表示验证通过，false 表示验证失败），message 为错误消息（如果验证失败，则包含错误消息，否则为 null）

## Inner Types

### Result

> Result 是一个不可变的记录类，用于表示验证结果。它包含两个字段：result 和 message。
> - result：一个布尔值，表示验证是否通过（true）或失败（false）。
> - message：一个字符串，表示验证失败时的错误消息，如果验证通过则为 null。

- **Type**: `record`
- **Fields**:
  - `result` (`boolean`): 验证结果（true 表示验证通过，false 表示验证失败）
  - `message` (`String`): 验证失败时的错误消息，如果验证通过则为 null
