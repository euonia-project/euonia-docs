# UserPrincipal

> Represents a user principal, wrapping a javax.security.auth.Subject and providing access to the subject's principals and claims.

- **Module**: `core`
- **Type**: `class`
- **Package**: `com.euonia.security`

## Methods

### UserPrincipal (constructor)

> Creates a new UserPrincipal with the given Subject.

- **Parameters**:
  - `subject` (`Subject`): The underlying security subject

### getSubject

> Returns the underlying Subject.

- **Returns**: `Subject` - The security subject

### getName

> Returns the name of the first Principal in the subject's principal set.

- **Returns**: `String` - The principal name, or null if none found

### getClaim

> Retrieves a claim value by claim type.

- **Parameters**:
  - `claimType` (`String`): The claim type to look up
- **Returns**: `String` - The claim value, or null if not found

### isAuthenticated

> 检查用户是否已认证。

- **Returns**: `boolean` - 如果已认证则返回 true

### hasRole

> 检查用户是否拥有指定角色。

- **Parameters**:
  - `role` (`String`): 角色名称
- **Returns**: `boolean` - 如果用户拥有该角色则返回 true

### isInRoles

> 检查用户是否拥有任意一个指定角色。

- **Parameters**:
  - `roles` (`String...`): 角色名称数组
- **Returns**: `boolean` - 如果用户拥有任意一个角色则返回 true

### ensureAuthenticated

> 确保用户已认证，否则抛出 AuthenticationException。

- **Throws**: `AuthenticationException` - 如果用户未认证

### ensureHasRole

> 确保用户拥有指定角色，否则抛出 UnauthorizedAccessException。

- **Parameters**:
  - `role` (`String`): 角色名称
- **Throws**: `AuthenticationException` - 如果用户未认证
- **Throws**: `UnauthorizedAccessException` - 如果用户不拥有该角色

### ensureInRoles

> 确保用户至少拥有其中一个指定角色，否则抛出 UnauthorizedAccessException。

- **Parameters**:
  - `roles` (`String...`): 角色名称数组
- **Throws**: `AuthenticationException` - 如果用户未认证
- **Throws**: `UnauthorizedAccessException` - 如果用户不拥有任意一个角色
