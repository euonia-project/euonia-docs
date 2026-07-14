# BusinessObjectFactory

> BusinessObjectFactory 是 ObjectFactory 接口的实现，使用反射基于带注解的工厂方法来创建、检索、插入、更新、保存、执行和删除业务对象。它支持与 bean 工厂集成以进行对象实例化，并根据保存操作处理不同的对象状态。

- **Type**: class
- **Package**: `com.euonia.factory`
- **Author**: damon(zhaorong@outlook.com)
- **Implements**: `ObjectFactory`

## Constructors

### BusinessObjectFactory(ServiceProvider provider)

> 使用指定的 ServiceProvider 构造一个新的 BusinessObjectFactory，ServiceProvider 可用于在对象创建和方法调用期间解析依赖。

**Parameters:**
- `provider` (`ServiceProvider`): 用于解析服务的 ServiceProvider

## Methods

### <T> create(Class<T> type, Object... criteria): T

> 通过查找并调用标注了 @FactoryCreate 的适当工厂方法，使用提供的条件作为参数来创建指定类型的实例。

**Parameters:**
- `type` (`Class<T>`): 要创建的对象的类
- `criteria` (`Object...`): 用于创建对象的参数

**Returns:** `T` — 创建的对象

### <T> fetch(Class<T> type, Object... criteria): T

> 通过查找并调用标注了 @FactoryFetch 的适当工厂方法，使用提供的条件作为参数来检索指定类型的实例。

**Parameters:**
- `type` (`Class<T>`): 要检索的对象的类
- `criteria` (`Object...`): 用于检索对象的参数

**Returns:** `T` — 检索到的对象

### <T> insert(Class<T> type, Object... criteria): T

> 通过查找并调用标注了 @FactoryInsert 的适当工厂方法，使用提供的条件作为参数来插入指定类型的新实例。

**Parameters:**
- `type` (`Class<T>`): 要插入的对象的类
- `criteria` (`Object...`): 用于插入对象的参数

**Returns:** `T` — 插入的对象

### <T> update(Class<T> type, Object... criteria): T

> 通过查找并调用标注了 @FactoryUpdate 的适当工厂方法，使用提供的条件作为参数来更新指定类型的现有实例。

**Parameters:**
- `type` (`Class<T>`): 要更新的对象的类
- `criteria` (`Object...`): 用于更新对象的参数

**Returns:** `T` — 更新后的对象

### <T> save(Class<T> type, T target): T

> 通过判断对象的状态并根据注解调用相应的工厂方法来保存提供的对象。根据对象状态（NEW/CHANGED/DELETED）分别调用 @FactoryInsert/@FactoryUpdate/@FactoryDelete 方法。

**Parameters:**
- `type` (`Class<T>`): 要保存的对象的类
- `target` (`T`): 要保存的对象实例

**Returns:** `T` — 保存后的对象

### <T> execute(Class<T> type, Object... criteria): T

> 通过查找并调用标注了 @FactoryExecute 的适当工厂方法，使用提供的条件作为参数来执行提供的对象。

**Parameters:**
- `type` (`Class<T>`): 要执行的对象的类
- `criteria` (`Object...`): 用于执行对象的参数

**Returns:** `T` — 执行后的对象

### <T> delete(Class<T> type, Object... criteria): void

> 通过查找并调用标注了 @FactoryDelete 的适当工厂方法，使用提供的条件作为参数来删除指定的对象。

**Parameters:**
- `type` (`Class<T>`): 要删除的对象的类
- `criteria` (`Object...`): 用于删除对象的参数
