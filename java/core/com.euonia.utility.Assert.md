# Assert

> Utility class providing assertion methods for validating method arguments and state.

- **Type**: class
- **Package**: `com.euonia.utility`

## Methods

### notNull

> Asserts that an object is not null.

- **Parameters**:
  - `obj` (`Object`): The object to check
  - `message` (`String`): The exception message if null
- **Throws**: `IllegalArgumentException` - If the object is null

### notNull

> Asserts that an object is not null, using a Supplier for the message.

- **Parameters**:
  - `obj` (`Object`): The object to check
  - `messageSupplier` (`Supplier<String>`): Supplier for the exception message if null
- **Throws**: `IllegalArgumentException` - If the object is null

### notEmpty

> Asserts that a string is not null, empty, or blank.

- **Parameters**:
  - `str` (`String`): The string to check
  - `message` (`String`): The exception message if empty
- **Throws**: `IllegalArgumentException` - If the string is null, empty, or blank

### notEmpty

> Asserts that a list is not null or empty.

- **Parameters**:
  - `list` (`List<?>`): The list to check
  - `message` (`String`): The exception message if empty
- **Throws**: `IllegalArgumentException` - If the list is null or empty

### notEmpty

> Asserts that an array is not null or empty.

- **Parameters**:
  - `array` (`Object[]`): The array to check
  - `message` (`String`): The exception message if empty
- **Throws**: `IllegalArgumentException` - If the array is null or empty

### notContains

> Asserts that a list does not contain any element matching the predicate.

- **Parameters**:
  - `list` (`List<T>`): The list to check
  - `predicate` (`Predicate<T>`): The predicate to test elements
  - `message` (`String`): The exception message if a match is found
- **Throws**: `IllegalArgumentException` - If any element matches

### notContains

> Asserts that an array does not contain any element matching the predicate.

- **Parameters**:
  - `array` (`T[]`): The array to check
  - `predicate` (`Predicate<T>`): The predicate to test elements
  - `message` (`String`): The exception message if a match is found
- **Throws**: `IllegalArgumentException` - If any element matches
