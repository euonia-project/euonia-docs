# TransportStrategyBuilder

> 传输策略构建器，提供流式 API 来配置消息传输的出站和入站规则。

- **Type**: interface
- **Package**: `com.euonia.bus.strategy`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### `getStrategy(): TransportStrategy`
> 获取构建完成的传输策略。

**Returns:** `TransportStrategy` — 构建完成的 `TransportStrategy` 实例

### `evaluateOutgoing(BiPredicate<String, Class<?>> predicate): TransportStrategyBuilder`
> 添加出站消息评估规则。

**Parameters:**
- `predicate` (`BiPredicate<String, Class<?>>`): 用于评估是否允许出站的断言

**Returns:** `TransportStrategyBuilder` — 当前 TransportStrategyBuilder 实例

### `evaluateIncoming(BiPredicate<String, Class<?>> predicate): TransportStrategyBuilder`
> 添加入站消息评估规则。

**Parameters:**
- `predicate` (`BiPredicate<String, Class<?>>`): 用于评估是否允许入站的断言

**Returns:** `TransportStrategyBuilder` — 当前 TransportStrategyBuilder 实例

### `<S extends TransportStrategy> add(S strategy): TransportStrategyBuilder`
> 添加传输策略实例。

**Type Parameters:**
- `<S>` — TransportStrategy 的类型

**Parameters:**
- `strategy` (`S`): 要添加的策略实例

**Returns:** `TransportStrategyBuilder` — 当前 TransportStrategyBuilder 实例

### `<S extends TransportStrategy> add(Class<S> strategyType): TransportStrategyBuilder`
> 添加传输策略类，将使用默认构造函数实例化。

**Type Parameters:**
- `<S>` — TransportStrategy 的类型

**Parameters:**
- `strategyType` (`Class<S>`): 要添加的策略类

**Returns:** `TransportStrategyBuilder` — 当前 TransportStrategyBuilder 实例
