# BusinessObject

> 业务对象的抽象基类，提供属性管理、规则检查、授权和属性变更通知等核心功能。

- **Type**: abstract class
- **Package**: `com.euonia.osba`
- **Author**: damon(zhaorong@outlook.com)
- **Type Parameters**: `<B extends BusinessObject<B>>` — 业务对象的具体类型
- **Implements**: `UseBusinessContext`, `RuleCheckable`, `AutoCloseable`

## Fields

| Field | Type | Description |
|-------|------|-------------|
| `support` | `PropertyChangeSupport` | 属性变更支持对象，用于触发属性变更事件 |

## Methods

### `setBusinessContext(BusinessContext businessContext): void`

> 设置业务上下文。

**Parameters:**
- `businessContext` (`BusinessContext`): 业务上下文

### `getBusinessContext(): BusinessContext`

> 获取业务上下文。

**Returns:** `BusinessContext` — 业务上下文

### `onBusinessContextSet(): void`

> 当业务上下文设置完成后调用。

### `initialize(): void`

> 初始化业务对象。

### `getFieldManager(): FieldDataManager`

> 获取字段数据管理器的实例。此方法使用双重检查锁定来确保线程安全地初始化字段数据管理器。

**Returns:** `FieldDataManager` — 字段数据管理器的实例

### `getRules(): Rules`

> 获取规则管理器的实例。此方法使用双重检查锁定来确保线程安全地初始化规则管理器。

**Returns:** `Rules` — 规则管理器的实例

### `addRules(): void`

> 添加自定义规则。

### `addRule(Rule rule): void`

> 添加规则到规则管理器。

**Parameters:**
- `rule` (`Rule`): 要添加的规则

### `<V> addRule(PropertyInfo<V> property, BiFunction<V, RuleContext, Boolean> rule, String message): void`

> 添加Lambda规则到规则管理器。

**Parameters:**
- `property` (`PropertyInfo<V>`): 属性信息
- `rule` (`BiFunction<V, RuleContext, Boolean>`): 规则函数
- `message` (`String`): 错误消息

### `<V> addRule(PropertyInfo<V> property, BiFunction<V, RuleContext, Boolean> rule, Function<V, String> messageFactory): void`

> 添加Lambda规则到规则管理器。

**Parameters:**
- `property` (`PropertyInfo<V>`): 属性信息
- `rule` (`BiFunction<V, RuleContext, Boolean>`): 规则函数
- `messageFactory` (`Function<V, String>`): 错误消息工厂

### `<V> addRequiredRule(PropertyInfo<V> property, String message): void`

> 添加必填规则到规则管理器。

**Parameters:**
- `property` (`PropertyInfo<V>`): 属性信息
- `message` (`String`): 错误消息

### `<V> addRequiredRule(PropertyInfo<V> property, Function<Object, String> messageFactory): void`

> 添加必填规则到规则管理器。

**Parameters:**
- `property` (`PropertyInfo<V>`): 属性信息
- `messageFactory` (`Function<Object, String>`): 错误消息工厂

### `checkPropertyRules(PropertyInfo<?> propertyInfo, Object oldValue, Object newValue): void`

> 检查指定属性的规则，并在规则检查完成后触发属性变更事件。

**Parameters:**
- `propertyInfo` (`PropertyInfo<?>`): 属性信息
- `oldValue` (`Object`): 属性的旧值
- `newValue` (`Object`): 属性的新值

### `isValid(): boolean`

> 获取业务对象的规则检查结果。

**Returns:** `boolean` — 如果对象有效，则返回 true；否则返回 false

### `ruleCheckComplete(PropertyInfo<?> property): void`

> 当规则检查完成时调用，触发属性变更事件。

**Parameters:**
- `property` (`PropertyInfo<?>`): 已完成规则检查的属性

### `ruleCheckComplete(String propertyName): void`

> 当规则检查完成时调用，触发属性变更事件。

**Parameters:**
- `propertyName` (`String`): 已完成规则检查的属性名称

### `allRulesComplete(): void`

> 当所有规则检查完成时调用，触发属性变更事件。

### `suspendRuleChecking(): void`

> 暂停规则检查。

### `resumeRuleChecking(): void`

> 恢复规则检查。

### `getBrokenRules(): BrokenRuleCollection`

> 获取破坏的规则集合。

**Returns:** `BrokenRuleCollection` — 破坏的规则集合

### `getPropertiesToCheckRulesOnChanged(): List<String>`

> 获取需要在属性变更时检查规则的属性列表。

**Returns:** `List<String>` — 需要在属性变更时检查规则的属性列表

### `getChangedProperties(): List<PropertyInfo<?>>`

> 获取已更改的属性列表。

**Returns:** `List<PropertyInfo<?>>` — 已更改的属性列表

### `hasChangedProperties(): boolean`

> 判断是否有已更改的属性。

**Returns:** `boolean` — 如果有已更改的属性，则返回 true；否则返回 false

### `addPropertyChangeListener(PropertyChangeListener listener): void`

> 添加属性变更监听器。

**Parameters:**
- `listener` (`PropertyChangeListener`): 要添加的属性变更监听器

### `removePropertyChangeListener(PropertyChangeListener listener): void`

> 移除属性变更监听器。

**Parameters:**
- `listener` (`PropertyChangeListener`): 要移除的属性变更监听器

### `onPropertyChanged(String propertyName, Object oldValue, Object newValue): void`

> 当属性值发生变化时调用，触发属性变更事件。

**Parameters:**
- `propertyName` (`String`): 属性的名称
- `oldValue` (`Object`): 属性的旧值
- `newValue` (`Object`): 属性的新值

### `onPropertyChanged(PropertyInfo<?> propertyInfo, Object oldValue, Object newValue): void`

> 当属性值发生变化时调用，触发属性变更事件。

**Parameters:**
- `propertyInfo` (`PropertyInfo<?>`): 属性信息
- `oldValue` (`Object`): 属性的旧值
- `newValue` (`Object`): 属性的新值

### `propertyHasChanged(PropertyInfo<?> propertyInfo, Object oldValue, Object newValue): void`

> 当属性值发生变化时调用，标记属性为已更改，并根据需要检查规则。

**Parameters:**
- `propertyInfo` (`PropertyInfo<?>`): 属性信息
- `oldValue` (`Object`): 属性的旧值
- `newValue` (`Object`): 属性的新值

### `fieldExists(PropertyInfo<?> propertyInfo): boolean`

> 检查指定属性的字段数据是否存在。

**Parameters:**
- `propertyInfo` (`PropertyInfo<?>`): 要检查的属性信息

**Returns:** `boolean` — 如果指定属性的字段数据存在则返回 true，否则返回 false

### `fieldExists(String fieldName): boolean`

> 检查指定字段名称的字段数据是否存在。

**Parameters:**
- `fieldName` (`String`): 要检查的字段名称

**Returns:** `boolean` — 如果指定字段名称的字段数据存在则返回 true，否则返回 false

### `<T> readProperty(PropertyInfo<T> propertyInfo): T`

> 读取指定属性的信息。

**Parameters:**
- `propertyInfo` (`PropertyInfo<T>`): 属性的信息

**Returns:** `T` — 指定属性的值

### `readProperty(String propertyName): Object`

> 读取指定名称的属性值。

**Parameters:**
- `propertyName` (`String`): 属性的名称

**Returns:** `Object` — 指定名称的属性值

### `<T> loadProperty(PropertyInfo<T> propertyInfo, T value): void`

> 加载属性值，如果属性值已存在，则使用现有值；否则使用属性的默认值。

**Parameters:**
- `propertyInfo` (`PropertyInfo<T>`): 属性的信息
- `value` (`T`): 要加载的值

### `<T> loadPropertyValue(PropertyInfo<T> propertyInfo, T oldValue, T newValue, boolean markAsChanged): void`

> 加载属性值。

**Parameters:**
- `propertyInfo` (`PropertyInfo<T>`): 属性的信息
- `oldValue` (`T`): 旧值
- `newValue` (`T`): 新值
- `markAsChanged` (`boolean`): 是否标记为已更改

### `<T> valuesDiffer(PropertyInfo<T> propertyInfo, T oldValue, T newValue): boolean`

> 判断两个属性值是否不同。

**Parameters:**
- `propertyInfo` (`PropertyInfo<T>`): 属性的信息
- `oldValue` (`T`): 旧值
- `newValue` (`T`): 新值

**Returns:** `boolean` — 如果属性值不同，返回 true；否则返回 false

### `canReadProperty(PropertyInfo<?> propertyInfo): boolean`

> 判断指定属性是否可读。

**Parameters:**
- `propertyInfo` (`PropertyInfo<?>`): 属性的信息

**Returns:** `boolean` — 如果属性可读，返回 true；否则返回 false

### `canReadProperty(String propertyName): boolean`

> 判断指定名称的属性是否可读。

**Parameters:**
- `propertyName` (`String`): 属性的名称

**Returns:** `boolean` — 如果属性可读，返回 true；否则返回 false

### `canReadProperty(PropertyInfo<?> propertyInfo, boolean throwOnFalse): boolean`

> 判断指定属性是否可读，并在属性不可读时抛出 UnauthorizedAccessException 异常。

**Parameters:**
- `propertyInfo` (`PropertyInfo<?>`): 属性的信息
- `throwOnFalse` (`boolean`): 如果为 true，当属性不可读时抛出异常

**Returns:** `boolean` — 如果属性可读，返回 true；否则返回 false

**Throws:** `UnauthorizedAccessException` — 当属性不可读且 throwOnFalse 为 true 时抛出

### `canReadProperty(String propertyName, boolean throwOnFalse): boolean`

> 判断指定名称的属性是否可读，并在属性不可读时抛出 UnauthorizedAccessException 异常。

**Parameters:**
- `propertyName` (`String`): 属性的名称
- `throwOnFalse` (`boolean`): 如果为 true，当属性不可读时抛出异常

**Returns:** `boolean` — 如果属性可读，返回 true；否则返回 false

**Throws:** `UnauthorizedAccessException` — 当属性不可读且 throwOnFalse 为 true 时抛出

### `canWriteProperty(PropertyInfo<?> propertyInfo): boolean`

> 判断指定属性是否可写。

**Parameters:**
- `propertyInfo` (`PropertyInfo<?>`): 属性的信息

**Returns:** `boolean` — 如果属性可写，返回 true；否则返回 false

### `canWriteProperty(PropertyInfo<?> propertyInfo, boolean throwOnFalse): boolean`

> 判断指定属性是否可写，并在属性不可写时抛出 UnauthorizedAccessException 异常。

**Parameters:**
- `propertyInfo` (`PropertyInfo<?>`): 属性的信息
- `throwOnFalse` (`boolean`): 如果为 true，当属性不可写时抛出异常

**Returns:** `boolean` — 如果属性可写，返回 true；否则返回 false

**Throws:** `UnauthorizedAccessException` — 当属性不可写且 throwOnFalse 为 true 时抛出

### `canWriteProperty(String propertyName): boolean`

> 判断指定名称的属性是否可写。

**Parameters:**
- `propertyName` (`String`): 属性的名称

**Returns:** `boolean` — 如果属性可写，返回 true；否则返回 false

### `canWriteProperty(String propertyName, boolean throwOnFalse): boolean`

> 判断指定名称的属性是否可写，并在属性不可写时抛出 UnauthorizedAccessException 异常。

**Parameters:**
- `propertyName` (`String`): 属性的名称
- `throwOnFalse` (`boolean`): 如果为 true，当属性不可写时抛出异常

**Returns:** `boolean` — 如果属性可写，返回 true；否则返回 false

**Throws:** `UnauthorizedAccessException` — 当属性不可写且 throwOnFalse 为 true 时抛出

### `isBypassingRuleCheck(): boolean`

> 判断当前业务对象是否正在绕过规则检查。

**Returns:** `boolean` — 如果正在绕过规则检查，则返回 true；否则返回 false

### `bypassRuleChecks(): BypassRuleCheckObject<B>`

> 创建一个新的 BypassRuleCheckObject 实例，并将其与当前业务对象关联，以绕过规则检查。

**Returns:** `BypassRuleCheckObject<B>` — 创建的 BypassRuleCheckObject 实例

### `<V> registerProperty(PropertyInfo<V> propertyInfo): PropertyInfo<V>`

> 使用指定的属性信息注册属性。

**Parameters:**
- `propertyInfo` (`PropertyInfo<V>`): 要注册的属性信息

**Returns:** `PropertyInfo<V>` — 已注册的属性信息

### `<V> registerProperty(Class<V> type, String propertyName): PropertyInfo<V>`

> 使用指定的类型和名称注册属性。

**Parameters:**
- `type` (`Class<V>`): 属性的类型
- `propertyName` (`String`): 属性的名称

**Returns:** `PropertyInfo<V>` — 已注册的属性信息

### `<V> registerProperty(Class<V> type, String propertyName, Supplier<V> defaultValue): PropertyInfo<V>`

> 使用指定的类型、名称和默认值注册属性。

**Parameters:**
- `type` (`Class<V>`): 属性的类型
- `propertyName` (`String`): 属性的名称
- `defaultValue` (`Supplier<V>`): 属性的默认值提供者

**Returns:** `PropertyInfo<V>` — 已注册的属性信息

### `<V> registerProperty(Class<V> type, String propertyName, String friendlyName): PropertyInfo<V>`

> 使用指定的类型、名称和友好名称注册属性。

**Parameters:**
- `type` (`Class<V>`): 属性的类型
- `propertyName` (`String`): 属性的名称
- `friendlyName` (`String`): 属性的友好名称

**Returns:** `PropertyInfo<V>` — 已注册的属性信息

### `<V> registerProperty(Class<V> type, String propertyName, String friendlyName, V defaultValue): PropertyInfo<V>`

> 使用指定的类型、名称、友好名称和默认值注册属性。

**Parameters:**
- `type` (`Class<V>`): 属性的类型
- `propertyName` (`String`): 属性的名称
- `friendlyName` (`String`): 属性的友好名称
- `defaultValue` (`V`): 属性的默认值

**Returns:** `PropertyInfo<V>` — 已注册的属性信息

### `<V> registerProperty(Class<V> type, String propertyName, String friendlyName, Supplier<V> defaultValue): PropertyInfo<V>`

> 使用指定的类型、名称、友好名称和默认值提供者注册属性。

**Parameters:**
- `type` (`Class<V>`): 属性的类型
- `propertyName` (`String`): 属性的名称
- `friendlyName` (`String`): 属性的友好名称
- `defaultValue` (`Supplier<V>`): 属性的默认值提供者

**Returns:** `PropertyInfo<V>` — 已注册的属性信息

### `close(): void`

> 关闭资源。

## Inner Classes

### BypassRuleCheckObject

> 用于绕过规则检查的对象。

- **Type**: static class
- **Type Parameters**: `<B extends BusinessObject<B>>` — 业务对象的类型
- **Implements**: `AutoCloseable`

#### Constructors

##### `BypassRuleCheckObject(BusinessObject<B> businessObject)`

> 创建一个新的 BypassRuleCheckObject 实例，并将其与指定的业务对象关联。

**Parameters:**
- `businessObject` (`BusinessObject<B>`): 要关联的业务对象

#### Methods

##### `static <B> create(BusinessObject<B> businessObject): BypassRuleCheckObject<B>`

> 创建一个新的 BypassRuleCheckObject 实例，并将其与指定的业务对象关联。

**Parameters:**
- `businessObject` (`BusinessObject<B>`): 要关联的业务对象

**Returns:** `BypassRuleCheckObject<B>` — 创建的 BypassRuleCheckObject 实例

##### `close(): void`

> 关闭 BypassRuleCheckObject 实例，减少引用计数，并在引用计数为零时重置业务对象的规则检查状态。
