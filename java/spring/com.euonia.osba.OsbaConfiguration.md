# OsbaConfiguration

> Spring `@Configuration` class that registers the `ObjectFactory` bean for the OSBA (Object Service Business Access) module, backed by a `BusinessObjectFactory` using the active `ServiceProvider`.

- **Type**: `@Configuration` class
- **Package**: `com.euonia.osba`
- **Author**: *(none specified)*

---

## Fields

*No fields — only `@Bean` factory methods.*

---

## Methods

### `objectFactory(ServiceProvider resolver)`

| Parameter | Type | Description |
|---|---|---|
| `resolver` | `ServiceProvider` | The service provider used to resolve dependencies within the factory |

Creates and returns a `BusinessObjectFactory` that delegates service resolution to the given `ServiceProvider`.

**Returns**: `ObjectFactory` — a new `BusinessObjectFactory(resolver)`.
