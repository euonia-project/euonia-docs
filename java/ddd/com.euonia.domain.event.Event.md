# Event

> {@link Event} 接口表示领域模型中的通用事件。定义了所有事件应具备的基本属性和方法。事件用于捕获和表示系统中的重要发生事件或变更，允许不同组件之间的通信和协调。

- **Type**: interface
- **Package**: `com.euonia.domain.event`
- **Author**: damon(zhaorong@outlook.com)

## Methods

### getSequence

> 获取事件的序号，可用于确定事件的顺序。

- **Returns**: `long` - 事件的序号

### setSequence

> 设置事件的序号，可用于确定事件的顺序。

- **Parameters**:
  - `sequence` (`long`): 事件的序号

### getEventIntent

> 获取事件意图，表示事件的目的或含义，可用于分类或识别正在处理的事件类型。

- **Returns**: `String` - 事件的意图

### setEventIntent

> 设置事件意图，表示事件的目的或含义，可用于分类或识别正在处理的事件类型。

- **Parameters**:
  - `eventIntent` (`String`): 事件的意图

### getOriginatorType

> 获取事件的发起者类型，表示事件的来源或起源。

- **Returns**: `String` - 事件的发起者类型

### setOriginatorType

> 设置事件的发起者类型，表示事件的来源或起源。

- **Parameters**:
  - `originatorType` (`String`): 事件的发起者类型

### getOriginatorId

> 获取事件的发起者 ID，唯一标识事件的来源或起源。

- **Returns**: `String` - 事件的发起者 ID

### setOriginatorId

> 设置事件的发起者 ID，唯一标识事件的来源或起源。

- **Parameters**:
  - `originatorId` (`String`): 事件的发起者 ID
