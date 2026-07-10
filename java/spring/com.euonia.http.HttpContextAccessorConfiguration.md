# HttpContextAccessorConfiguration

> Configuration for request context related beans.

- **Type**: `@Configuration` class
- **Package**: `com.euonia.http`
- **Author**: *(none specified)*

---

## Fields

*No fields — only `@Bean` factory methods.*

---

## Methods

### `requestContextAccessor()`

| Parameter | Type | Description |
|---|---|---|
| *(none)* | | |

Creates and returns the singleton `DefaultRequestContextAccessor` instance via `DefaultRequestContextAccessor.getInstance()`.

**Returns**: `RequestContextAccessor` — the global `DefaultRequestContextAccessor`.
