# AccountException

> Exception thrown for account-related errors during authentication or authorization processes, such as account not found, account locked, etc. This exception can be extended to provide more specific error types.

- **Type**: class
- **Package**: `com.euonia.security`

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `identity` | `Object` | The identity associated with the account error |
| `details` | `Map<String, Object>` | Additional details about the error |

## Methods

### AccountException (constructor)

> Creates a new AccountException with the specified identity.

- **Parameters**:
  - `identity` (`Object`): The identity associated with the account error, such as username or user ID

### AccountException (constructor)

> Creates a new AccountException with the specified identity and detail message.

- **Parameters**:
  - `identity` (`Object`): The identity associated with the account error
  - `message` (`String`): The detail message explaining the reason for the exception

### AccountException (constructor)

> Creates a new AccountException with the specified identity, detail message, and cause.

- **Parameters**:
  - `identity` (`Object`): The identity associated with the account error
  - `message` (`String`): The detail message explaining the reason for the exception
  - `cause` (`Throwable`): The cause of the exception
