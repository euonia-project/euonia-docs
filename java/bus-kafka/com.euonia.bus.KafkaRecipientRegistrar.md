# KafkaRecipientRegistrar

> Kafka 消息接收者注册器，负责根据已注册的 `ChannelRegistration` 列表创建并启动对应的 Kafka 消费者实例。

- **Type**: `public class`
- **Package**: `com.euonia.bus`
- **Author**: `damon(zhaorong@outlook.com)`
- **Implements**: `RecipientRegistrar`

## Fields

| Name | Type | Description |
|------|------|-------------|
| `LOGGER` | `Logger` | 日志记录器 |
| `provider` | `ServiceProvider` | 服务提供者 |
| `options` | `KafkaBusOptions` | Kafka 总线配置选项 |
| `convention` | `MessageConvention` | 消息约定 |
| `strategy` | `TransportStrategy` | 传输策略 |
| `recipients` | `List<KafkaRecipient>` | 已创建的消息接收者列表 |

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `KafkaRecipientRegistrar` | `KafkaRecipientRegistrar(Configurator configurator, ServiceProvider provider, KafkaBusOptions options)` | 构造器；从 configurator 获取 MessageConvention，从 strategy builders 获取 TransportStrategy |
| `register` | `void register(Map<String, ChannelRegistration> registrations, String defaultTransport)` | 遍历所有注册的 channel，根据约定（多播/单播/请求）创建对应的 KafkaRecipient 并启动 |
| `close` | `void close()` | 关闭所有已注册的接收者并清空列表 |
