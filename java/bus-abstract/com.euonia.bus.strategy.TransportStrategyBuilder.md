# TransportStrategyBuilder

> Builder interface for constructing a `TransportStrategy` using fluent API methods to evaluate outgoing/incoming predicates and add custom strategies.

- **Type**: interface
- **Package**: `com.euonia.bus.strategy`

## Methods

### getStrategy

> Gets the TransportStrategy instance that has been built by this builder.

- **Returns**: `TransportStrategy` - the built TransportStrategy instance

### evaluateOutgoing

> Adds an outgoing evaluation predicate.

- **Parameters**:
  - `predicate` (`BiPredicate<String, Class<?>>`): the predicate to evaluate outgoing messages
- **Returns**: `TransportStrategyBuilder` - the current instance

### evaluateIncoming

> Adds an incoming evaluation predicate.

- **Parameters**:
  - `predicate` (`BiPredicate<String, Class<?>>`): the predicate to evaluate incoming messages
- **Returns**: `TransportStrategyBuilder` - the current instance

### add

> Adds a TransportStrategy instance.

- **Parameters**:
  - `strategy` (`S extends TransportStrategy`): the strategy to add
- **Returns**: `TransportStrategyBuilder` - the current instance

### add

> Adds a TransportStrategy by class (instantiated via default constructor).

- **Parameters**:
  - `strategyType` (`Class<S>`): the strategy class to add
- **Returns**: `TransportStrategyBuilder` - the current instance
