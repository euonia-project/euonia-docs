# UserPrincipal

> Represents a user principal, wrapping a javax.security.auth.Subject and providing access to the subject's principals and claims.

- **Type**: class
- **Package**: `com.euonia.security`

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `subject` | `Subject` | The underlying javax.security.auth.Subject |

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
