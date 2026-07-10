# ApplicationContextServiceProvider

> Spring `ApplicationContext`-backed implementation of `ServiceProvider`. Resolves services, provided types with generic type arguments, named beans, and dynamically creates and autowires instances via the Spring `AutowireCapableBeanFactory`.

- **Type**: Class implementing `ServiceProvider`
- **Package**: `com.euonia.reflection`
- **Author**: *(none specified)*

---

## Fields

| Name | Type | Description |
|---|---|---|
| `context` | `ApplicationContext` | The Spring application context used for bean resolution |

---

## Methods

### Constructor — `ApplicationContextServiceProvider(ApplicationContext context)`

| Parameter | Type | Description |
|---|---|---|
| `context` | `ApplicationContext` | The Spring application context |

### `getService(Class<T> type)`

| Parameter | Type | Description |
|---|---|---|
| `type` | `Class<T>` | The service type to resolve |

Returns an `Optional` containing the bean if available, or `Optional.empty()` if none is found. Uses `context.getBeanProvider(type).getIfAvailable()`.

**Returns**: `Optional<T>`

---

### `getService(Class<T> type, Class<?>... genericTypeArguments)`

| Parameter | Type | Description |
|---|---|---|
| `type` | `Class<T>` | The service type |
| `genericTypeArguments` | `Class<?>...` | Generic type arguments for the bean |

Resolves beans matching the given type with generic type arguments and returns the first match, or `Optional.empty()`.

**Returns**: `Optional<T>`

---

### `getService(Class<T> type, String serviceName)`

| Parameter | Type | Description |
|---|---|---|
| `type` | `Class<T>` | The service type |
| `serviceName` | `String` | The bean name |

Looks up a bean by name among beans of the given type.

**Returns**: `Optional<T>`

---

### `getRequiredService(Class<T> type)`

| Parameter | Type | Description |
|---|---|---|
| `type` | `Class<T>` | The required service type |

Returns the required bean directly via `context.getBean(type)`. Throws if not found.

**Returns**: `T`

---

### `getServices(Class<T> type)`

| Parameter | Type | Description |
|---|---|---|
| `type` | `Class<T>` | The service type |

Returns all beans of the given type (including non-singletons and eagerly initialized beans) as a `List<T>`.

**Returns**: `List<T>`

---

### `getServices(Class<T> type, Class<?>... genericTypeArguments)`

| Parameter | Type | Description |
|---|---|---|
| `type` | `Class<T>` | The service type |
| `genericTypeArguments` | `Class<?>...` | Generic type arguments for resolution |

Resolves beans by `ResolvableType.forClassWithGenerics` and returns all matching beans as a `List<T>`.

**Returns**: `List<T>`

---

### `createInstance(Class<T> type, Object... constructorArguments)`

| Parameter | Type | Description |
|---|---|---|
| `type` | `Class<T>` | The type to instantiate |
| `constructorArguments` | `Object...` | Constructor arguments for matching |

Creates and autowires an instance of the given type. If no constructor arguments are provided, uses `AutowireCapableBeanFactory.createBean(type)`. Otherwise, finds a matching constructor by checking parameter count and assignability (with primitive boxing), instantiates via `BeanUtils.instantiateClass`, then autowires and initializes via the factory.

**Throws**: `IllegalStateException` — if no matching constructor is found.

**Returns**: `T` — a fully autowired instance.

---

### `isAssignable(Class<?>[] parameterTypes, Object[] args)` *(private static)*

| Parameter | Type | Description |
|---|---|---|
| `parameterTypes` | `Class<?>[]` | Expected parameter types |
| `args` | `Object[]` | Actual argument values |

Checks assignability, boxing primitives via `TypeHelper.boxIfPrimitive` and skipping `null` arguments.

**Returns**: `boolean` — `true` if all non-null arguments are assignable.
