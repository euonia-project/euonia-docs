# Spring 模块 — 开发者手册

> Spring 集成模块，为 Euonia 各核心模块提供 Spring Boot 自动配置，包括 ServiceProvider、Pipeline、MessageBus、OSBA 和 UnitOfWork 的 Spring Bean 注册与 AOP 切面支持。

- **Maven 坐标**: `com.euonia:spring`
- **依赖**: core, osba, pipeline, bus-core, uow, Spring Framework
- **API文档**：[点击查看](./apis)

---

## 核心功能

### ApplicationContextServiceProvider

基于 Spring `ApplicationContext` 实现 Euonia 的 `ServiceProvider` 接口，提供 7 种服务解析方法：

```java
@Service
public class OrderService {
    @Autowired
    private ServiceProvider provider;
    
    public void process() {
        var repo = provider.getRequiredService(OrderRepository.class);
        var bus = provider.getService(Bus.class);
    }
}
```

### 自动配置清单

| 配置类 | 注册的 Bean |
|--------|-----------|
| `ServiceProviderConfiguration` | `ApplicationContextServiceProvider` |
| `MessageBusConfiguration` | `Bus`, `HandlerContext` |
| `PipelineConfiguration` | `PipelineFactory`, `Pipeline` (prototype), `PipelineDelegate` (prototype) |
| `OsbaConfiguration` | `ObjectFactory`, `BusinessObjectFactory` |
| `HttpContextAccessorConfiguration` | `RequestContextAccessor` |
| `UnitOfWorkAutoConfiguration` | `UnitOfWorkManager`, `UnitOfWorkOptions` + `@EnableAspectJAutoProxy` |
| `UnitOfWorkAspect` | `@Around("@annotation(UnitOfWork)")` 环绕通知 |

### @UnitOfWork AOP 切面

```java
@Service
public class OrderService {
    
    @com.euonia.uow.annotation.UnitOfWork(isTransactional = true)
    public Order createOrder(CreateOrderCommand cmd) {
        // 方法执行前自动 begin() 工作单元
        // 方法执行后自动 completeAsync()
        // 异常时自动触发 onFailure()
    }
}
```

---

## 配置

Spring Boot 应用无需额外配置，所有 `@Configuration` 类通过自动配置机制生效：

```java
@SpringBootApplication
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

---

## Maven

```xml
<dependency>
    <groupId>com.euonia</groupId>
    <artifactId>spring</artifactId>
    <version>${euonia.version}</version>
</dependency>
```

---

## 依赖

- `com.euonia:core`, `com.euonia:osba`, `com.euonia:pipeline`
- `com.euonia:bus-core`, `com.euonia:uow`
- `org.springframework`

## 作者

damon (zhaorong@outlook.com)
