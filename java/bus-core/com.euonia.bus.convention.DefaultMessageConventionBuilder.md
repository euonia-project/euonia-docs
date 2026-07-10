# DefaultMessageConventionBuilder
> Default implementation of the `MessageConventionBuilder` interface. It provides methods to define message conventions for unicast, multicast, and request messages.
- **Type**: class
- **Package**: `com.euonia.bus.convention`
- **Author**: (not specified)

## Fields
| Field | Type | Description |
|-------|------|-------------|
| `convention` | `BaseMessageConvention` | 基础消息约定实例 |

## Methods
### getConvention
> Gets the MessageConvention instance that has been built by this builder.
- **Returns**: `MessageConvention` - the built MessageConvention instance

### evaluateUnicast
> Adds a message convention that will be used to evaluate whether a type is a unicast message.
- **Parameters**:
  - `predicate` (`Predicate<String>`): the predicate to evaluate the unicast message type
- **Returns**: `MessageConventionBuilder` - the current instance

### evaluateMulticast
> Adds a message convention that will be used to evaluate whether a type is a multicast message.
- **Parameters**:
  - `predicate` (`Predicate<String>`): the predicate to evaluate the multicast message type
- **Returns**: `MessageConventionBuilder` - the current instance

### evaluateRequest
> Adds a message convention that will be used to evaluate whether a type is a request message.
- **Parameters**:
  - `predicate` (`Predicate<String>`): the predicate to evaluate the request message type
- **Returns**: `MessageConventionBuilder` - the current instance

### evaluate
> Adds a message convention that will be used to evaluate whether a type is a unicast, multicast, or request message.
- **Parameters**:
  - `convention` (`Function<String, MessageConventionType>`): the function to evaluate the message type
- **Returns**: `MessageConventionBuilder` - the current instance

### add
> Adds a message convention instance.
- **Parameters**:
  - `convention` (`C extends MessageConvention`): the MessageConvention instance to add
- **Returns**: `MessageConventionBuilder` - the current instance

### add
> Adds a message convention by class, instantiated using its default constructor.
- **Parameters**:
  - `conventionClass` (`Class<C>`): the class of the MessageConvention to add
- **Returns**: `MessageConventionBuilder` - the current instance
