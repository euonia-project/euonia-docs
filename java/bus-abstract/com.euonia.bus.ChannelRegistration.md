# ChannelRegistration

> ChannelRegistration represents the registration of a message handler for a specific channel and message type.

- **Type**: class
- **Package**: `com.euonia.bus`

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `messageType` | `Class<?>` | The message type this registration handles. |
| `handlers` | `List<ChannelHandler>` | The list of registered handlers. |

## Methods

### ChannelRegistration

> Constructs a new ChannelRegistration for the given message type.

- **Parameters**:
  - `messageType` (`Class<?>`): the message type

### getMessageType

- **Returns**: `Class<?>` - the message type

### getHandlers

- **Returns**: `List<ChannelHandler>` - an unmodifiable list of registered handlers

### addHandler

> Adds a handler to this registration.

- **Parameters**:
  - `handler` (`ChannelHandler`): the handler to add
- **Returns**: `ChannelRegistration` - this instance, for chaining
