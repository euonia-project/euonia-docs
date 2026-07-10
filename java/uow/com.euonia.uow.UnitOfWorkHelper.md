# UnitOfWorkHelper
> 用于检查类型和方法上工作单元注解和标记接口的静态工具方法。主要由 AOP 拦截器和代理使用，用于判断给定的类或方法是否应被包装在工作单元中。
- **Type**: class
- **Package**: `com.euonia.uow`
- **Author**: damon(zhaorong@outlook.com)

## Fields
*No public fields.*

## Methods

### isUnitOfWorkType
> 如果类型具有工作单元注解（类或方法级别）或实现了 UnitOfWorkEnabled，则返回 true。
- **Parameters**: `implementationType` (`Class<?>`): 要检查的类型
- **Returns**: boolean - 如果类型需要工作单元则返回 true

### isUnitOfWorkMethod
> 如果方法具有活跃的（未禁用的）@UnitOfWork 注解，则返回 true。
- **Parameters**: `method` (`Method`): 要检查的方法
- **Returns**: boolean - 如果方法标注了 @UnitOfWork 则返回 true

### getUnitOfWorkAnnotation
> 从方法或其声明类中检索活跃的 @UnitOfWork 注解。如果注解不存在或 disabled，则返回 null。
- **Parameters**: `method` (`Method`): 要检查的方法
- **Returns**: UnitOfWork - 注解，或 null
