# RabbitMqRecipientRegistrar

> RabbitMQ 消息接收者注册器，负责根据已注册的 `ChannelRegistration` 列表创建并启动对应的 RabbitMQ 消费者实例。根据消息约定判断消息类型，分别创建：多播类型 → `RabbitMqTopicSubscriber`、单播类型 → `RabbitMqQueueConsumer`、请求类型 → `RabbitMqRequestExecutor`。

- **Type:** `public class` implements `RecipientRegistrar`
- **Package:** `com.euonia.bus`
- **Author:** damon(zhaorong@outlook.com)

## Fields

| Name | Type | Description |
|------|------|-------------|
| `recipients` | `private final List<RabbitMqRecipient>` | 已创建的接收者列表，用于生命周期管理 |
| `provider` | `private final ServiceProvider` | 服务提供者，用于解析依赖服务 |
| `options` | `private final RabbitMqBusOptions` | RabbitMQ 总线选项 |
| `convention` | `private final MessageConvention` | 消息约定，用于判断消息类型（单播/多播/请求） |
| `strategy` | `private final TransportStrategy` | 传输策略，用于判断消息是否应由当前传输实例处理 |

## Methods

| Name | Return | Description |
|------|--------|-------------|
| `RabbitMqRecipientRegistrar(Configurator, ServiceProvider, RabbitMqBusOptions)` | (constructor) | 使用指定的配置器、服务提供者和 RabbitMQ 选项构造注册器 |
| `register(Map<String, ChannelRegistration>, String)` | `void` | 遍历注册列表，根据约定判断消息类型（多播/单播/请求），创建对应的 RabbitMQ 消费者实例（TopicSubscriber/QueueConsumer/RequestExecutor），注册日志监听器（INFO 级别），启动并加入生命周期管理 |
| `close()` | `void` | 关闭所有已创建的接收者，停止消息监听并释放 Channel 资源 |
