# ServiceProviderConfiguration

> Spring `@Configuration` class that registers the `ServiceProvider` bean, backed by an `ApplicationContextServiceProvider` wrapping the Spring `ApplicationContext`.

- **Type**: `@Configuration` class
- **Package**: `com.euonia.reflection`
- **Author**: *(none specified)*

---

## Fields

*No fields — only `@Bean` factory methods.*

---

## Methods

### `serviceProvider(ApplicationContext applicationContext)`

| Parameter | Type | Description |
|---|---|---|
| `applicationContext` | `ApplicationContext` | The Spring application context |

Creates and returns an `ApplicationContextServiceProvider` that delegates all service resolution to the given `ApplicationContext`.

**Returns**: `ServiceProvider` — a new `ApplicationContextServiceProvider(applicationContext)`.
