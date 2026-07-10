# UnitOfWorkAspect

> Spring AOP aspect that intercepts methods annotated with `@UnitOfWork` and wraps them in a unit of work.
>
> **How it works**:
> 1. Before the method executes, a new `UnitOfWork` is begun via `UnitOfWorkManager`.
> 2. The method proceeds normally.
> 3. On success, the unit of work is completed (save → handlers → listeners).
> 4. On failure, the unit of work is rolled back and the exception is propagated. Failed listeners are fired via `UnitOfWork#close()`.
> 5. The unit of work is always disposed in a `finally` block.
>
> **Pointcut**: Intercepts any Spring-managed bean method whose class or method is annotated with `@UnitOfWork`. Methods annotated with `@UnitOfWork(disabled = true)` are skipped.

- **Type**: `@Aspect` class
- **Package**: `com.euonia.uow`
- **Author**: *(none specified)*
- **See**: `UnitOfWorkManager`, `com.euonia.uow.annotation.UnitOfWork`

---

## Fields

| Name | Type | Description |
|---|---|---|
| `unitOfWorkManager` | `UnitOfWorkManager` | The unit-of-work manager used for lifecycle operations |

---

## Methods

### Constructor — `UnitOfWorkAspect(UnitOfWorkManager unitOfWorkManager)`

| Parameter | Type | Description |
|---|---|---|
| `unitOfWorkManager` | `UnitOfWorkManager` | the unit-of-work manager |

Creates an aspect that uses the given manager for unit-of-work lifecycle.

---

### `aroundUnitOfWork(ProceedingJoinPoint pjp)`

| Parameter | Type | Description |
|---|---|---|
| `pjp` | `ProceedingJoinPoint` | the join point |

Around advice that wraps annotated methods in a unit of work.

- **Pointcut**: `@within(com.euonia.uow.annotation.UnitOfWork) || @annotation(com.euonia.uow.annotation.UnitOfWork)`
- Skips methods where `UnitOfWorkHelper.isUnitOfWorkMethod(method)` returns `false` (e.g., `@UnitOfWork(disabled = true)`).
- On success: begins a new `UnitOfWork`, proceeds with the method, then calls `uow.completeAsync().toCompletableFuture().join()`.
- On failure: the `try-with-resources` block detects the unit of work was not completed and fires failed listeners automatically via `close()`.

**Returns**: `Object` — the method's return value.

**Throws**: `Throwable` — if the method throws.
