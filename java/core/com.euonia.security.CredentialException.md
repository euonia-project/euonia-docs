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

### getCredential

> 获取导致异常的凭证。

- **Returns**: `Object` - 导致异常的凭证

### getDetails

> 获取异常相关的额外详细信息。

- **Returns**: `Map<String, Object>` - 详细信息的映射

### get

> 根据键从详细信息中获取特定的值。

- **Parameters**:
  - `key` (`String`): 要检索的键
- **Returns**: `Object` - 与键关联的值，如果键不存在则返回 null

### set

> 在详细信息中设置键值对。

- **Parameters**:
  - `key` (`String`): 键
  - `value` (`Object`): 值

### with

> 在详细信息中设置键值对，并返回当前实例支持链式调用。

- **Parameters**:
  - `key` (`String`): 键
  - `value` (`Object`): 值
- **Returns**: `CredentialException` - 当前 CredentialException 实例
