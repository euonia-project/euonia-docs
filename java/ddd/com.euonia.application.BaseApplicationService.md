# BaseApplicationService

> {@link BaseApplicationService} 是应用服务的抽象基类，提供通用功能。它实现了 {@link ApplicationService} 接口，并使用 {@link ServiceProvider} 来访问其他服务，例如代表当前已认证用户的 {@link UserPrincipal}。具体的应用服务实现可以继承此类，从而获得解析服务和访问用户信息的能力，无需在每个服务中实现这些功能。

- **Type**: abstract class
- **Package**: `com.euonia.application`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `provider` | `ServiceProvider` | 服务提供者 |

## Methods

### BaseApplicationService

> 使用指定的服务提供者构造基类实例。

- **Parameters**:
  - `provider` (`ServiceProvider`): 服务提供者

### getService

> 从 {@link ServiceProvider} 中解析指定类型的服务。

- **Parameters**:
  - `type` (`Class<T>`): 要解析的服务类类型
- **Returns**: `Optional<T>` - 包含已解析服务的 {@link Optional}，如果服务不可用则为空

### getUser

> 从 {@link ServiceProvider} 中获取当前已认证的用户。

- **Returns**: `UserPrincipal` - 当前已认证的用户，如果不可用则为 null
