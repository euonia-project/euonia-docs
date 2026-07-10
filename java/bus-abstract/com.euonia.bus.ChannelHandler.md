# ChannelHandler

> Represents a message handler, encapsulating the handler type, method, and instance.

- **Type**: record
- **Package**: `com.euonia.bus`

## Record Components

| Component | Type | Description |
|-----------|------|-------------|
| `handlerType` | `Class<?>` | the type of the handler |
| `method` | `Method` | the method to be invoked |
| `instance` | `Object` | the instance of the handler |
