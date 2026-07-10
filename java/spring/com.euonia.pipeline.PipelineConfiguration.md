# PipelineConfiguration

> 管道 Spring 配置类，负责注册管道相关的 Bean。
>
> 配置以下 Bean：
> - `PipelineFactory` —— 管道工厂，用于创建管道实例
> - `Pipeline` —— 管道实例，用于编排消息处理步骤
> - `PipelineDelegate` —— 管道委托，封装已构建的管道执行入口
>
> 所有 Bean 均以原型作用域注册，确保每次注入都获得新实例。

- **Type**: `@Configuration` class
- **Package**: `com.euonia.pipeline`
- **Author**: damon (zhaorong@outlook.com)

---

## Fields

*No fields — only `@Bean` factory methods.*

---

## Methods

### `pipelineFactory(ServiceProvider resolver)`

| Parameter | Type | Description |
|---|---|---|
| `resolver` | `ServiceProvider` | 服务提供者，用于依赖解析 |

注册 `PipelineFactory` Bean，使用默认的管道工厂实现。

- **Scope**: `prototype`

**Returns**: `PipelineFactory` — 默认管道工厂实例（`DefaultPipelineFactory`）。

---

### `pipeline(ServiceProvider resolver)`

| Parameter | Type | Description |
|---|---|---|
| `resolver` | `ServiceProvider` | 服务提供者，用于依赖解析 |

注册 `Pipeline` Bean，使用默认的管道提供者实现。

- **Scope**: `prototype`

**Returns**: `Pipeline` — 默认管道实例（`DefaultPipelineProvider`）。

---

### `pipelineDelegate(Pipeline pipeline)`

| Parameter | Type | Description |
|---|---|---|
| `pipeline` | `Pipeline` | 用于构建委托的管道实例 |

注册 `PipelineDelegate` Bean，从已构建的管道生成委托。

- **Scope**: `prototype`

**Returns**: `PipelineDelegate` — 封装已构建管道的管道委托（`pipeline.build()`）。
