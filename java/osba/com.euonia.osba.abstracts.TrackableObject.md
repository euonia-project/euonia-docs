# TrackableObject

> TrackableObject 是一个接口，定义了用于跟踪对象状态的方法，包括其有效性、变更、删除状态以及是否为新建对象或是否可保存。此接口通常用于业务对象中，以管理其生命周期，并确保在执行保存或删除等操作之前对象处于一致的状态。

- **Type**: interface
- **Package**: `com.euonia.osba.abstracts`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### isValid(): boolean

> 指示对象是否处于有效状态。用于确定对象是否可以保存。

**Returns:** `boolean` — 如果对象有效则返回 true，否则返回 false

### isChanged(): boolean

> 指示对象自上次保存以来是否已被更改。

**Returns:** `boolean` — 如果对象已被更改则返回 true，否则返回 false

### isDeleted(): boolean

> 指示对象是否已被标记为删除。

**Returns:** `boolean` — 如果对象已被标记为删除则返回 true，否则返回 false

### isNew(): boolean

> 指示对象是否为新建对象且尚未保存。

**Returns:** `boolean` — 如果对象是新建对象则返回 true，否则返回 false

### isSavable(): boolean

> 指示对象是否可以保存。

**Returns:** `boolean` — 如果对象可以保存则返回 true，否则返回 false

### isBusy(): boolean

> 指示对象当前是否处于忙碌状态，即正在执行不应被中断的操作，如保存或删除。

**Returns:** `boolean` — 如果对象处于忙碌状态则返回 true，否则返回 false
