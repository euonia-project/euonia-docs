# RecipientRegistrar

> `RecipientRegistrar` 负责将处理器注册信息注册到接收者系统中。
> 提供了将处理器注册列表与默认传输一起注册的方法。
> <p>
> 此接口抽象了注册过程，允许不同的实现处理处理器注册的具体方式以及如何使用默认传输。
> <p>
> 此接口的实现可能会与各种接收者类型（如订阅者、执行器）进行交互，
> 并管理处理器注册的生命周期，确保它们被正确注册并可用于消息分发。

- **Type**: interface
- **Package**: `com.euonia.bus.recipient`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### `register(Map<String, ChannelRegistration> registrations, String defaultTransport): void`

> 使用指定的默认传输将处理器注册信息注册到接收者系统中。

**Parameters:**
- `registrations` (`Map<String, ChannelRegistration>`): 要注册的处理器注册信息
- `defaultTransport` (`String`): 要使用的默认传输
