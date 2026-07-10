# MessageBusConfiguration

> Spring `@Configuration` class that registers the core message bus beans: `Bus` and `HandlerContext`. It wires recipient registrars into the configurator and uses reflection to register generic handlers that implement `Handler<TMessage, MessageContext>`.

- **Type**: `@Configuration` class
- **Package**: `com.euonia.bus`
- **Author**: *(none specified)*

---

## Fields

*No fields — only `@Bean` factory methods.*

---

## Methods

### `bus(ServiceProvider provider, Configurator configurator)`

| Parameter | Type | Description |
|---|---|---|
| `provider` | `ServiceProvider` | The service provider used to resolve `RecipientRegistrar` implementations |
| `configurator` | `Configurator` | The bus configurator holding channel registrations and default transport |

Creates and returns a `MessageBus` instance. Before constructing the bus, all `RecipientRegistrar` services are resolved from the provider and their `register(...)` method is called with the configurator's registrations and default transport.

**Assertions**: Both `provider` and `configurator` must not be null.

**Returns**: `Bus` — a new `MessageBus` instance.

---

### `handlerContext(ServiceProvider provider, Configurator configurator)`

| Parameter | Type | Description |
|---|---|---|
| `provider` | `ServiceProvider` | The service provider |
| `configurator` | `Configurator` | The bus configurator holding channel→handler mappings |

Creates and returns a `DefaultHandlerContext`. For each channel registration, it inspects each handler type to determine whether it implements `Handler<TMessage, MessageContext>` directly via generic interface introspection. If so, the handler is registered via the reflective `register(String, Class, Class)` method; otherwise the fallback `register(String, ChannelRegistration.HandlerReference)` overload is used.

**Assertions**: Both `provider` and `configurator` must not be null.

**Returns**: `HandlerContext` — a fully populated `DefaultHandlerContext`.

**Throws**: `RuntimeException` — if reflective access to the register method fails.
