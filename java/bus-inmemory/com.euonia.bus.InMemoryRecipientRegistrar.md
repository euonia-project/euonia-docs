# InMemoryRecipientRegistrar

> 内存消息总线的接收者注册器。负责将消息处理器注册到对应的内存消息传输实例。根据消息约定（`MessageConvention`），将消息类型分类为单播、多播或请求类型，并分别注册到 `StrongReferenceMessenger`。

- **Type**: `class` (implements `RecipientRegistrar`)
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Fields

| Name | Type | Modifiers | Description |
|------|------|-----------|-------------|
| `provider` | `ServiceProvider` | `private final` | 服务提供者，用于创建接收者实例。 |
| `options` | `InMemoryBusOptions` | `private final` | 内存总线配置选项。 |
| `convention` | `MessageConvention` | `private final` | 消息约定，用于判断消息类型（单播/多播/请求）。 |
| `strategy` | `TransportStrategy` | `private final` | 传输策略，用于判断消息是否应由当前传输实例处理。 |
| `registrationCache` | `ConcurrentMap<Class<?>, InMemoryRecipient>` | `private final` | 接收者注册缓存，避免重复创建（当不允许多实例时）。 |

## Methods

| Name | Return Type | Parameters | Description |
|------|-------------|------------|-------------|
| `InMemoryRecipientRegistrar` *(constructor)* | — | `Configurator configurator, ServiceProvider provider, InMemoryBusOptions options` | 创建内存接收者注册器。 |
| `register` | `void` | `Map<String, ChannelRegistration> registrations, String defaultTransport` | 将消息处理器注册到对应的内存消息传输实例。 |
| `getRecipient` | `<T extends InMemoryRecipient> T` | `Class<T> type` | 获取或创建指定类型的接收者实例。根据 `multipleSubscriberInstance` 选项决定是否缓存。 |
