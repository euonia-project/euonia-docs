# SimpleServiceProvider

> SimpleServiceProvider is a basic implementation of the ServiceProvider interface that uses a ConcurrentHashMap to store and retrieve service instances. It allows for registering services and creating new instances using reflection.

- **Type**: class
- **Package**: `com.euonia.reflection`

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `services` | `Map<Class<?>, Object>` | ConcurrentHashMap storing registered service instances |

## Methods

### register

> Registers a service instance for the given type.

- **Parameters**:
  - `type` (`Class<T>`): The service type
  - `instance` (`T`): The service instance

### getService

> Retrieves a service instance of the specified type.

- **Parameters**:
  - `type` (`Class<T>`): The service class
- **Returns**: `Optional<T>` - Optional containing the service instance, or empty if not found

### getService

> Retrieves a service instance of the specified type with generic type arguments.

- **Parameters**:
  - `type` (`Class<T>`): The service class
  - `genericTypeArguments` (`Class<?>...`): The generic type arguments
- **Returns**: `Optional<T>` - Always empty for this implementation

### getService

> Retrieves a service instance of the specified type and service name.

- **Parameters**:
  - `type` (`Class<T>`): The service class
  - `serviceName` (`String`): The service name
- **Returns**: `Optional<T>` - Optional containing the service instance, or empty if not found

### getRequiredService

> Gets the required service instance, throwing if not found.

- **Parameters**:
  - `type` (`Class<T>`): The service class
- **Returns**: `T` - The service instance
- **Throws**: `IllegalStateException` - If service is not found

### getServices

> Gets all services of the specified type.

- **Parameters**:
  - `type` (`Class<T>`): The service class
- **Returns**: `List<T>` - Always an empty list for this implementation

### getServices

> Gets all services of the specified type with generic type arguments.

- **Parameters**:
  - `type` (`Class<T>`): The service class
  - `genericTypeArguments` (`Class<?>...`): The generic type arguments
- **Returns**: `List<T>` - Always an empty list for this implementation

### createInstance

> Creates an instance of the specified type using reflection, matching constructor arguments.

- **Parameters**:
  - `type` (`Class<T>`): The type to instantiate
  - `constructorArguments` (`Object...`): The constructor arguments
- **Returns**: `T` - The newly created instance
