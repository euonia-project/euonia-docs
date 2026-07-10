# BaseTransportStrategy
> Represents a composite transport strategy that aggregates multiple `TransportStrategy` instances and caches the results of outgoing and incoming channel evaluations using `ConcurrentHashMap`. The composite strategy allows for flexible configuration by enabling the addition of custom transport strategies and the definition of custom predicates.
- **Type**: class
- **Package**: `com.euonia.bus.strategy`
- **Author**: (not specified)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `defaultStrategy` | `OverridableTransportStrategy` | 可覆盖的默认策略 |
| `strategies` | `List<TransportStrategy>` | 已注册的策略列表 |
| `outgoingCache` | `StrategyCache` | 发送判定缓存 |
| `incomingCache` | `StrategyCache` | 接收判定缓存 |

## Methods
### BaseTransportStrategy
> 构造方法，初始化时添加默认可覆盖策略。

### getName
> 获取策略名称。
- **Returns**: `String` - "Composite transport strategy"

### allowOutgoing
> 判断指定通道和消息类型是否允许发送。
- **Parameters**:
  - `channel` (`String`): 通道名
  - `messageType` (`Class<?>`): 消息类型
- **Returns**: `boolean` - 是否允许

### allowIncoming
> 判断指定通道和消息类型是否允许接收。
- **Parameters**:
  - `channel` (`String`): 通道名
  - `messageType` (`Class<?>`): 消息类型
- **Returns**: `boolean` - 是否允许

### add
> Adds one or more transport strategies to the composite strategy.
- **Parameters**:
  - `strategies` (`TransportStrategy...`): the transport strategies to add

### defineOutgoingStrategy
> Defines a custom strategy for evaluating outgoing channels.
- **Parameters**:
  - `strategy` (`BiPredicate<String, Class<?>>`): a predicate that determines if a channel is considered outgoing

### defineIncomingStrategy
> Defines a custom strategy for evaluating incoming channels.
- **Parameters**:
  - `strategy` (`BiPredicate<String, Class<?>>`): a predicate that determines if a channel is considered incoming
