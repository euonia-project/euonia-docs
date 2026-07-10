# CredentialException

> The CredentialException is thrown when there is an issue with user credentials, such as invalid username or password. This exception indicates that the provided credentials are incorrect or do not meet the required criteria.

- **Module**: `core`
- **Type**: `abstract class`
- **Package**: `com.euonia.security`
- **Extends**: `RuntimeException`

## Methods

### CredentialException (constructor)

> Creates a new CredentialException with the specified credential.

- **Parameters**:
  - `credential` (`Object`): The credential that caused the exception

### CredentialException (constructor)

> Creates a new CredentialException with the specified credential and message.

- **Parameters**:
  - `credential` (`Object`): The credential that caused the exception
  - `message` (`String`): The detail message for the exception

### CredentialException (constructor)

> Creates a new CredentialException with the specified credential, message, and cause.

- **Parameters**:
  - `credential` (`Object`): The credential that caused the exception
  - `message` (`String`): The detail message for the exception
  - `cause` (`Throwable`): The cause of the exception
