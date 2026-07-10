# BadGatewayException

> The BadGatewayException is thrown when an HTTP request results in a 502 Bad Gateway status code. This exception indicates that the server, while acting as a gateway or proxy, received an invalid response from the upstream server.

- **Module**: `core`
- **Type**: `class`
- **Package**: `com.euonia.http`
- **Extends**: [`HttpStatusException`](./com.euonia.http.HttpStatusException.md)

## Methods

### BadGatewayException (constructor)

> Creates a new BadGatewayException with the specified message.

- **Parameters**:
  - `message` (`String`): The detail message for the exception

### BadGatewayException (constructor)

> Creates a new BadGatewayException with the specified message and cause.

- **Parameters**:
  - `message` (`String`): The detail message for the exception
  - `cause` (`Throwable`): The cause of the exception
