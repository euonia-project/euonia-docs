# KafkaBusOptions

> Kafka 总线传输的配置选项。封装 Kafka 生产者/消费者配置以及 Euonia 特定的消息处理参数。

- **Type**: `public final class`
- **Package**: `com.euonia.bus`
- **Author**: `damon(zhaorong@outlook.com)`

## Fields

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `name` | `String` | `KafkaTransport.class.getSimpleName()` | 传输名称 |
| `bootstrapServers` | `String` | `"localhost:9092"` | Kafka bootstrap 服务器地址 |
| `topicPrefix` | `String` | `KafkaConstants.DEFAULT_TOPIC_PREFIX` | Topic 前缀 |
| `groupId` | `String` | `System.getProperty("euonia.kafka.groupId", "euonia-consumer")` | 消费者组 ID |
| `concurrency` | `int` | `1` | 并发消费者数量 |
| `retryDelay` | `long` | `5000L` | 重试延迟（毫秒） |
| `retryAttempts` | `int` | `3` | 重试次数 |
| `producerConfig` | `Map<String, Object>` | `{key.serializer=StringSerializer, value.serializer=ByteArraySerializer}` | Kafka 生产者配置 |
| `consumerConfig` | `Map<String, Object>` | `{key.deserializer=StringDeserializer, value.deserializer=ByteArrayDeserializer, enable.auto.commit=false}` | Kafka 消费者配置 |
| `subscriptionId` | `String` | `null` | 订阅 ID |

## Methods

| Name | Signature | Description |
|------|-----------|-------------|
| `getName` | `String getName()` | 获取传输名称 |
| `setName` | `void setName(String name)` | 设置传输名称 |
| `getBootstrapServers` | `String getBootstrapServers()` | 获取 bootstrap 服务器地址 |
| `setBootstrapServers` | `void setBootstrapServers(String bootstrapServers)` | 设置 bootstrap 服务器地址 |
| `getTopicPrefix` | `String getTopicPrefix()` | 获取 topic 前缀 |
| `setTopicPrefix` | `void setTopicPrefix(String topicPrefix)` | 设置 topic 前缀 |
| `getGroupId` | `String getGroupId()` | 获取消费者组 ID |
| `setGroupId` | `void setGroupId(String groupId)` | 设置消费者组 ID |
| `getConcurrency` | `int getConcurrency()` | 获取并发消费者数量 |
| `setConcurrency` | `void setConcurrency(int concurrency)` | 设置并发消费者数量 |
| `getRetryDelay` | `long getRetryDelay()` | 获取重试延迟 |
| `setRetryDelay` | `void setRetryDelay(long retryDelay)` | 设置重试延迟 |
| `getRetryAttempts` | `int getRetryAttempts()` | 获取重试次数 |
| `setRetryAttempts` | `void setRetryAttempts(int retryAttempts)` | 设置重试次数 |
| `getProducerConfig` | `Map<String, Object> getProducerConfig()` | 获取生产者配置 |
| `setProducerConfig` | `void setProducerConfig(Map<String, Object> producerConfig)` | 设置生产者配置 |
| `getConsumerConfig` | `Map<String, Object> getConsumerConfig()` | 获取消费者配置 |
| `setConsumerConfig` | `void setConsumerConfig(Map<String, Object> consumerConfig)` | 设置消费者配置 |
| `getSubscriptionId` | `String getSubscriptionId()` | 获取订阅 ID |
| `setSubscriptionId` | `void setSubscriptionId(String subscriptionId)` | 设置订阅 ID |
| `generateTopicName` | `String generateTopicName(String channelName)` | 生成 Kafka 主题名称 |
