# ExecutableObject

> 表示可执行的业务对象。该类继承自 BusinessObject 类，为 execute 和 create 方法提供了默认实现，子类可以重写这些方法以提供特定的行为。

- **Type**: abstract class
- **Package**: `com.euonia.osba`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<T extends ExecutableObject<T>>` — 业务对象的类型，必须继承自 ExecutableObject
- **Extends**: `BusinessObject<T>`

## Methods

### execute

> 执行业务对象的操作。默认实现不执行任何操作，子类可以重写此方法以提供特定的行为。

### create

> 创建业务对象的操作。默认实现不执行任何操作，子类可以重写此方法以提供特定的行为。
