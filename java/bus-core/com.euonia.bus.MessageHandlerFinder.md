# MessageHandlerFinder
> 消息处理器查找器，负责扫描指定包或处理器类型并生成 `ChannelRegistration` 列表。
- **Type**: class
- **Package**: `com.euonia.bus`
- **Author**: damon(zhaorong@outlook.com)

## Description
支持两种查找方式：
- 按包扫描 —— 扫描指定包下所有类中标注了 `@Subscribe` 注解的方法
- 按类型解析 —— 解析指定的处理器类型，同时支持 `@Subscribe` 注解方法和 `Handler` 接口实现

## Inner Types
### Delegate
> 委托函数式接口，用于接收找到的处理器注册信息。
- **Type**: interface
- **Methods**:
  - `next(String channel, Class<?> messageType, ChannelHandler handler)`: 接收通道名、消息类型和处理器

## Methods
### find
> 扫描指定包下的所有类，查找其中带有 `@Subscribe` 注解的方法，并为每个匹配的方法生成一个 `ChannelRegistration`。
- **Parameters**:
  - `delegate` (`Delegate`): 委托回调
  - `packages` (`String...`): 要扫描的包名数组

### find
> 解析指定的处理器类型，同时查找 `@Subscribe` 注解方法和 `Handler` 接口实现，并为每个匹配的方法生成一个 `ChannelRegistration`。
- **Parameters**:
  - `delegate` (`Delegate`): 委托回调
  - `handlerTypes` (`Class<?>...`): 要解析的处理器类型数组
