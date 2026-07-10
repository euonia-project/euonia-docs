# GenericType

> An abstract class for capturing and retaining generic type information at runtime. Enables type-safe generic resolution by extracting the actual type argument from a subclass.

- **Type**: class
- **Package**: `com.euonia.reflection`

## Methods

### GenericType (constructor)

> Creates a GenericType instance. If no explicit type is provided, the constructor extracts the actual type argument from the subclass hierarchy.

### getType

> Returns the captured generic type.

- **Returns**: `Type` - The generic type

### forType

> Creates a GenericType for the given Type.

- **Parameters**:
  - `type` (`Type`): The type to wrap
- **Returns**: `GenericType<T>` - A new GenericType instance

### equals

> Compares this GenericType with another object for equality based on the captured type.

- **Parameters**:
  - `other` (`Object`): The object to compare with
- **Returns**: `boolean` - true if equal

### hashCode

> Returns the hash code of the captured type.

- **Returns**: `int` - The hash code

### toString

> Returns a string representation of the GenericType.

- **Returns**: `String` - String representation
