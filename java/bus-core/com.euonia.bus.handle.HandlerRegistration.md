# HandlerRegistration
> 处理器注册记录，包含处理器类型和处理器工厂。
- **Type**: record
- **Package**: `com.euonia.bus.handle`
- **Author**: (not specified)

## Record Components
| Component | Type | Description |
|-----------|------|-------------|
| `handlerType` | `Class<?>` | 处理器类型 |
| `factory` | `HandlerFactory` | 处理器委托工厂 |
