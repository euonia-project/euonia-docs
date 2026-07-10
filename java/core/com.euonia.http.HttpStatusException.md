# HttpStatusException

> The HttpStatusException is thrown when an HTTP request results in an error status code. It contains the HTTP status code and a message describing the error. This exception can be used to represent various HTTP errors, such as 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 500 Internal Server Error, etc.

- **Type**: class
- **Package**: `com.euonia.http`

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `statusCode` | `int` | The HTTP status code |

## Methods

### HttpStatusException (constructor)

> Creates a new HttpStatusException with the specified status code and message.

- **Parameters**:
  - `statusCode` (`int`): The HTTP status code
  - `message` (`String`): The detail message for the exception

### HttpStatusException (constructor)

> Creates a new HttpStatusException with the specified status code, message, and cause.

- **Parameters**:
  - `statusCode` (`int`): The HTTP status code
  - `message` (`String`): The detail message for the exception
  - `cause` (`Throwable`): The cause of the exception

### getStatusCode

> Returns the HTTP status code.

- **Returns**: `int` - The HTTP status code
