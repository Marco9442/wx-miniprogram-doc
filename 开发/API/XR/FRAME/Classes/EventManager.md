[xr-frame](./../) / [Exports](./../modules.html) / EventManager

# [#](#Class-EventManager) Class: EventManager

事件管理器。

每个`Element`都有自己的事件管理器，通过参数可以触发到`xml`。

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./EventManager.html#constructor)

### [#](#Properties) Properties

- [isEventManager](./EventManager.html#isEventManager)

### [#](#Methods) Methods

- [add](./EventManager.html#add)
- [addOnce](./EventManager.html#addOnce)
- [clear](./EventManager.html#clear)
- [flush](./EventManager.html#flush)
- [flushAll](./EventManager.html#flushAll)
- [has](./EventManager.html#has)
- [remove](./EventManager.html#remove)
- [trigger](./EventManager.html#trigger)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new EventManager**(`_el`, `_triggerElementEvent`)

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `_el` | [`Element`](./Element.html) |
| `_triggerElementEvent` | `TFrameworkEventTrigger` |

## [#](#Properties-2) Properties

### [#](#isEventManager) isEventManager

• **isEventManager**: `boolean` = `true`

## [#](#Methods-2) Methods

### [#](#add) add

▸ **add**<`TEvent`>(`type`, `callback`, `priority?`): [`EventManager`](./EventManager.html)

添加一个事件监听器。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `TEvent` | `any` |

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `type` | `string` |
| `callback` | [`TEventCallback`](./../modules.html#TEventCallback)<`TEvent`> |
| `priority?` | `number` |

#### [#](#Returns) Returns

[`EventManager`](./EventManager.html)

---

### [#](#addOnce) addOnce

▸ **addOnce**<`TEvent`>(`type`, `callback`, `priority?`): [`EventManager`](./EventManager.html)

添加一个事件监听器，触发一次后自动移除。

#### [#](#Type-parameters-2) Type parameters

| Name | Type |
| --- | --- |
| `TEvent` | `any` |

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `type` | `string` |
| `callback` | [`TEventCallback`](./../modules.html#TEventCallback)<`TEvent`> |
| `priority?` | `number` |

#### [#](#Returns-2) Returns

[`EventManager`](./EventManager.html)

---

### [#](#clear) clear

▸ **clear**(`type`): [`EventManager`](./EventManager.html)

清空某事件的所有监听器。

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `type` | `string` |

#### [#](#Returns-3) Returns

[`EventManager`](./EventManager.html)

---

### [#](#flush) flush

▸ **flush**(`type`): [`EventManager`](./EventManager.html)

分发某个缓存的事件，一般不需要自行触发。

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `type` | `string` |

#### [#](#Returns-4) Returns

[`EventManager`](./EventManager.html)

---

### [#](#flushAll) flushAll

▸ **flushAll**(): [`EventManager`](./EventManager.html)

分发所有缓存的事件，一般不需要自行触发。

#### [#](#Returns-5) Returns

[`EventManager`](./EventManager.html)

---

### [#](#has) has

▸ **has**(`type`): `boolean`

判断一个事件是否被注册。
注册是指用户绑定过了至少一个事件处理器，无论是来自于wxml还是JS。

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `type` | `string` |

#### [#](#Returns-6) Returns

`boolean`

---

### [#](#remove) remove

▸ **remove**<`TEvent`>(`type`, `callback`): [`EventManager`](./EventManager.html)

移除一个事件监听器。

#### [#](#Type-parameters-3) Type parameters

| Name | Type |
| --- | --- |
| `TEvent` | `any` |

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `type` | `string` |
| `callback` | [`TEventCallback`](./../modules.html#TEventCallback)<`TEvent`> |

#### [#](#Returns-7) Returns

[`EventManager`](./EventManager.html)

---

### [#](#trigger) trigger

▸ **trigger**<`TEvent`>(`type`, `event?`, `immediately?`, `toXML?`, `bubbles?`): [`EventManager`](./EventManager.html)

触发一个事件。

#### [#](#Type-parameters-4) Type parameters

| Name | Type |
| --- | --- |
| `TEvent` | `any` |

#### [#](#Parameters-8) Parameters

| Name | Type | Default value | Description |
| --- | --- | --- | --- |
| `type` | `string` | `undefined` | 要触发的事件类型。 |
| `event?` | `TEvent` | `undefined` | 事件的值。 |
| `immediately` | `boolean` | `true` | 是否要将事件立即分发，如果不则会先缓存，之后在每一帧更新前统一分发，避免不必要的分发。 |
| `toXML` | `boolean` | `true` | 是否要派发到`xml`绑定的事件中。 |
| `bubbles` | `boolean` | `false` | 是否要进行事件冒泡。 |

#### [#](#Returns-8) Returns

[`EventManager`](./EventManager.html)

Incorrect translation.