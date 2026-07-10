# DefaultTransportStrategyBuilder
> `TransportStrategyBuilder` 接口的默认实现，提供流式 API 来配置传输策略。
- **Type**: class
- **Package**: `com.euonia.bus.strategy`
- **Author**: (not specified)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `strategy` | `BaseTransportStrategy` | 基础传输策略实例 |

## Methods
### getStrategy
> 获取已构建的 TransportStrategy 实例。
- **Returns**: `TransportStrategy` - the built TransportStrategy instance

### evaluateOutgoing
> 添加判断消息是否允许发送的谓词。
- **Parameters**:
  - `predicate` (`BiPredicate<String, Class<?>>`): 判断谓词
- **Returns**: `TransportStrategyBuilder` - 当前实例

### evaluateIncoming
> 添加判断消息是否允许接收的谓词。
- **Parameters**:
  - `predicate` (`BiPredicate<String, Class<?>>`): 判断谓词
- **Returns**: `TransportStrategyBuilder` - 当前实例

### add
> 添加传输策略实例。
- **Parameters**:
  - `strategy` (`S extends TransportStrategy`): 传输策略实例
- **Returns**: `TransportStrategyBuilder` - 当前实例

### add
> 通过 Class 添加传输策略（通过反射实例化）。
- **Parameters**:
  - `strategyType` (`Class<S>`): 传输策略类型
- **Returns**: `TransportStrategyBuilder` - 当前实例
