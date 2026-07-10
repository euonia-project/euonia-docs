# InboxStore
> 收件箱（Inbox）持久化接口，用于消息去重（幂等性）。
- **Type**: interface
- **Package**: `com.euonia.bus.consistency`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### insert
> 插入一条消息到收件箱。
- **Parameters**:
  - `channel` (`String`): 消息通道
  - `message` (`MessageEnvelope<T>`): 消息内容
  - `handlers` (`List<String>`): 处理器列表
- **Returns**: `boolean` — 插入是否成功

### insert
> 插入一条消息到收件箱。
- **Parameters**:
  - `entry` (`InboxEntry`): 消息条目
- **Returns**: `boolean` — 插入是否成功

### markAsSuccess
> 标记消息处理成功。
- **Parameters**:
  - `messageId` (`String`): 消息ID
  - `handler` (`String`): 处理器

### markAsFailed
> 标记消息处理失败。
- **Parameters**:
  - `messageId` (`String`): 消息ID
  - `handler` (`String`): 处理器
  - `errorMessage` (`String`): 错误信息

### get
> 获取收件箱条目。
- **Parameters**:
  - `messageId` (`String`): 消息ID
- **Returns**: `InboxEntry` — 收件箱条目

### getAndCache
> 获取收件箱条目并缓存。
- **Parameters**:
  - `messageId` (`String`): 消息ID
- **Returns**: `InboxEntry` — 收件箱条目

### clearCache
> 清除缓存。

### getFailedMessages
> 获取处理失败的消息列表。
- **Returns**: `List<InboxHandle>` — 处理失败的消息列表