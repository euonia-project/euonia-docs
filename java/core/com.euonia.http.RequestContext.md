# RequestContext

> 包含当前请求的相关信息。

- **Type**: class
- **Package**: `com.euonia.http`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `connectionId` | `String` | 表示连接的唯一标识符 |
| `requestUri` | `String` | 请求的 URI |
| `requestMethod` | `String` | 请求的方法（如 GET、POST 等） |
| `remoteIpAddress` | `String` | 远程目标的 IP 地址 |
| `remotePort` | `int` | 远程目标的端口 |
| `webSocketRequest` | `boolean` | 指示该请求是否为 WebSocket 建立请求 |
| `user` | `UserPrincipal` | 当前用户主体 |
| `requestHeaders` | `Map<String, String>` | 请求头信息 |
| `traceIdentifier` | `String` | 追踪标识符 |

## Methods

### getConnectionId

> 获取表示连接的唯一标识符。

- **Returns**: `String` - 连接标识符

### setConnectionId

> 设置表示连接的唯一标识符。

- **Parameters**:
  - `connectionId` (`String`): 连接标识符

### getRequestUri

> 获取请求的 URI。

- **Returns**: `String` - 请求 URI

### setRequestUri

> 设置请求的 URI。

- **Parameters**:
  - `requestUri` (`String`): 请求 URI

### getRequestMethod

> 获取请求的方法（如 GET、POST 等）。

- **Returns**: `String` - 请求方法

### setRequestMethod

> 设置请求的方法（如 GET、POST 等）。

- **Parameters**:
  - `requestMethod` (`String`): 请求方法

### getRemoteIpAddress

> 获取远程目标的 IP 地址。

- **Returns**: `String` - 远程 IP 地址

### setRemoteIpAddress

> 设置远程目标的 IP 地址。

- **Parameters**:
  - `remoteIpAddress` (`String`): 远程 IP 地址

### getRemotePort

> 获取远程目标的端口。

- **Returns**: `int` - 远程端口

### setRemotePort

> 设置远程目标的端口。

- **Parameters**:
  - `remotePort` (`int`): 远程端口

### isWebSocketRequest

> 获取一个值，指示该请求是否为 WebSocket 建立请求。

- **Returns**: `boolean` - 是否为 WebSocket 请求

### setWebSocketRequest

> 设置一个值，指示该请求是否为 WebSocket 建立请求。

- **Parameters**:
  - `webSocketRequest` (`boolean`): 是否为 WebSocket 请求

### getUser

> 获取当前用户主体。

- **Returns**: `UserPrincipal` - 用户主体

### setUser

> 设置当前用户主体。

- **Parameters**:
  - `user` (`UserPrincipal`): 用户主体

### getRequestHeaders

> 获取请求头信息。

- **Returns**: `Map<String, String>` - 请求头

### setRequestHeaders

> 设置请求头信息。

- **Parameters**:
  - `requestHeaders` (`Map<String, String>`): 请求头

### getTraceIdentifier

> 获取追踪标识符。

- **Returns**: `String` - 追踪标识符

### setTraceIdentifier

> 设置追踪标识符。

- **Parameters**:
  - `traceIdentifier` (`String`): 追踪标识符
