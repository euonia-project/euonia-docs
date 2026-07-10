# PipelineBehaviors

> PipelineBehaviors 注解用于标记一个类，指定与该类相关的管道行为组件。该注解包含一个 value 属性，它是一个 Class<?> 数组，表示与该类相关的管道行为组件的类型。

- **Type**: annotation
- **Package**: `com.euonia.pipeline`
- **Author**: damon(zhaorong@outlook.com)

## Elements

| Element | Type | Default | Description |
|---------|------|---------|-------------|
| `value` | `Class<?>[]` | (required) | 与该类相关的管道行为组件的类型数组 |
