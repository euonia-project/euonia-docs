# TransportStrategy

> Defines the contract for a transport strategy, which determines how messages are handled for outgoing and incoming operations.

- **Type**: interface
- **Package**: `com.euonia.bus.strategy`

## Methods

### getName

> Gets the name of the transport strategy.

- **Returns**: `String` - the name of the transport strategy

### allowOutgoing

> Determines if the transport strategy allows outgoing messages on the specified channel.

- **Parameters**:
  - `channel` (`String`): the channel name
  - `messageType` (`Class<?>`): the type of the message
- **Returns**: `boolean` - true if the transport strategy allows outgoing messages on the specified channel, false otherwise

### allowIncoming

> Determines if the transport strategy allows incoming messages on the specified channel.

- **Parameters**:
  - `channel` (`String`): the channel name
  - `messageType` (`Class<?>`): the type of the message
- **Returns**: `boolean` - true if the transport strategy allows incoming messages on the specified channel, false otherwise
