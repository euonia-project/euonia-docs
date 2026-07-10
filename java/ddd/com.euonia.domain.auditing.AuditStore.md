# AuditStore

> 审计记录存储接口。实现类可以选择将记录存储到数据库、文件系统或任何其他存储机制中。{@code save} 方法是泛型的，可以处理任何继承自 {@link AuditRecord} 的审计记录类型，从而灵活支持不同类型的记录。ID 类型也是泛型的，允许使用不同类型的标识符（如 Long、String、UUID 等）。

- **Type**: interface
- **Package**: `com.euonia.domain.auditing`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### save

> 保存审计记录。

- **Parameters**:
  - `record` (`T`): 要保存的审计记录
