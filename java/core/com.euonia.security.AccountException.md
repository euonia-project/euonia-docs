# AccountException

> Exception thrown for account-related errors during authentication or authorization processes, such as account not found, account locked, etc. This exception can be extended to provide more specific error types.

- **Module**: `core`
- **Type**: `abstract class`
- **Package**: `com.euonia.security`
- **Extends**: `RuntimeException`

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

### getIdentity

> 获取与错误关联的账户标识。

- **Returns**: `Object` - 账户标识

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
- **Returns**: `AccountException` - 当前 AccountException 实例
