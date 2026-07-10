# BeanScope

> Defines the scopes of a bean in the Spring IoC container.
>
> The scopes are defined as constants in this class, and can be used to specify the scope of a bean when defining it in the Spring configuration.
>
> The scopes defined in this class are:
> - `APPLICATION` — Scopes a single bean definition to the lifecycle of a ServletContext. Only valid in the context of a web-aware Spring ApplicationContext.
> - `PROTOTYPE` — Scopes a single bean definition to any number of object instances.
> - `REQUEST` — Scopes a single bean definition to the lifecycle of a single HTTP request. Only valid in the context of a web-aware Spring ApplicationContext.
> - `SESSION` — Scopes a single bean definition to the lifecycle of an HTTP Session. Only valid in the context of a web-aware Spring ApplicationContext.
> - `SINGLETON` — Scopes a single bean definition to a single object instance for each Spring IoC container.
> - `WEB_SOCKET` — Scopes a single bean definition to the lifecycle of a WebSocket. Only valid in the context of a web-aware Spring ApplicationContext.

- **Type**: Constants class
- **Package**: `com.euonia.spring`
- **Author**: *(none specified)*

---

## Fields

| Name | Type | Value | Description |
|---|---|---|---|
| `APPLICATION` | `String` | `"application"` | Scopes a single bean definition to the lifecycle of a ServletContext. Only valid in the context of a web-aware Spring ApplicationContext. |
| `PROTOTYPE` | `String` | `"prototype"` | Scopes a single bean definition to any number of object instances. |
| `REQUEST` | `String` | `"request"` | Scopes a single bean definition to the lifecycle of a single HTTP request. That is, each HTTP request has its own instance of a bean created off the back of a single bean definition. Only valid in the context of a web-aware Spring ApplicationContext. |
| `SESSION` | `String` | `"session"` | Scopes a single bean definition to the lifecycle of an HTTP Session. Only valid in the context of a web-aware Spring ApplicationContext. |
| `SINGLETON` | `String` | `"singleton"` | Scopes a single bean definition to a single object instance for each Spring IoC container. |
| `WEB_SOCKET` | `String` | `"websocket"` | Scopes a single bean definition to the lifecycle of a WebSocket. Only valid in the context of a web-aware Spring ApplicationContext. |

---

## Methods

*No methods — constants-only utility class. A commented-out enum-based implementation exists in the source.*
