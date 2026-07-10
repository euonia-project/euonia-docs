# UnitOfWorkAutoConfiguration

> Spring auto-configuration for the Unit of Work module.
>
> Registers the following beans:
> - `UnitOfWorkAccessor` — thread-local holder for the ambient unit of work
> - `UnitOfWorkManager` — entry point for creating and managing units of work
> - `UnitOfWorkAspect` — AOP aspect that wraps `@UnitOfWork`-annotated methods
>
> Enable AspectJ auto-proxy so the `UnitOfWorkAspect` can intercept annotated Spring beans.
>
> **Usage**: For Spring Boot, this configuration is auto-detected via `spring.factories`. For plain Spring, import it manually:
> ```java
> @Configuration
> @Import(UnitOfWorkAutoConfiguration.class)
> public class AppConfig { }
> ```

- **Type**: `@Configuration` class with `@EnableAspectJAutoProxy`
- **Package**: `com.euonia.uow`
- **Author**: *(none specified)*
- **See**: `UnitOfWorkAspect`, `UnitOfWorkManager`

---

## Fields

*No fields — only `@Bean` factory methods.*

---

## Methods

### `unitOfWorkAccessor()`

| Parameter | Type | Description |
|---|---|---|
| *(none)* | | |

Creates the thread-local accessor for tracking the ambient unit of work.

**Returns**: `UnitOfWorkAccessor` — a new `UnitOfWorkAccessor()`.

---

### `unitOfWorkManager(UnitOfWorkAccessor accessor)`

| Parameter | Type | Description |
|---|---|---|
| `accessor` | `UnitOfWorkAccessor` | the thread-local accessor |

Creates the unit-of-work manager.

**Returns**: `UnitOfWorkManager` — a new `UnitOfWorkManager(accessor, new UnitOfWorkOptions())`.

---

### `unitOfWorkAspect(UnitOfWorkManager manager)`

| Parameter | Type | Description |
|---|---|---|
| `manager` | `UnitOfWorkManager` | the unit-of-work manager |

Creates the AOP aspect that wraps `@UnitOfWork`-annotated methods in a unit of work.

**Returns**: `UnitOfWorkAspect` — a new `UnitOfWorkAspect(manager)`.
