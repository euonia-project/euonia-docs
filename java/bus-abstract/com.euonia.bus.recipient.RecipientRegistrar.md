# RecipientRegistrar

> RecipientRegistrar is responsible for registering handler registrations with the recipient system. It provides a method to register a list of handler registrations along with a default transport.
>
> This interface abstracts the registration process, allowing different implementations to handle the specifics of how handlers are registered and how the default transport is utilized.
>
> Implementations of this interface may interact with various recipient types (e.g., Subscribers, Executors) and may manage the lifecycle of handler registrations, ensuring that they are properly registered and available for message dispatching.

- **Type**: interface
- **Package**: `com.euonia.bus.recipient`

## Methods

### register

> Registers the given handler registrations with the recipient system, using the specified default transport.

- **Parameters**:
  - `registrations` (`Map<String, ChannelRegistration>`): the handler registrations to register
  - `defaultTransport` (`String`): the default transport to use
