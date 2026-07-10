# UnitOfWork
> 标记某个类型或方法需要工作单元支持。当应用于类上时，所有方法都会被包装在工作单元中。当应用于方法上时，仅该特定方法会被包装。
- **Type**: annotation
- **Package**: `com.euonia.uow.annotation`
- **Author**: damon(zhaorong@outlook.com)

## Elements

| Element | Type | Description |
|---------|------|-------------|
| `disabled` | `boolean` | 当设置为 true 时，即使父作用域声明了工作单元，也会为被注解的元素抑制工作单元 |
