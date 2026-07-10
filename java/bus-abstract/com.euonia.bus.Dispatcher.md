# Dispatcher

> Defines a dispatcher that determines handler types for messages.

- **Type**: interface
- **Package**: `com.euonia.bus`

## Methods

### determine

> Determine the transport(s) to which the message of the given channel should be dispatched.

- **Parameters**:
  - `channel` (`String`): the channel of the message
  - `messageType` (`Class<?>`): the type of the message
- **Returns**: `List<String>` - a list of transport names
