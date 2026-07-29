[xr-frame](./../) / [Exports](./../modules.html) / ShareSystem

# [#](#Class-ShareSystem) Class: ShareSystem

分享系统，负责分享相关功能。

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`IShareSystemData`](./../interfaces/IShareSystemData.html)>

  ↳ **`ShareSystem`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./ShareSystem.html#constructor)

### [#](#Events) Events

- [onAdd](./ShareSystem.html#onAdd)
- [onRelease](./ShareSystem.html#onRelease)
- [onRemove](./ShareSystem.html#onRemove)
- [onTick](./ShareSystem.html#onTick)
- [onUpdate](./ShareSystem.html#onUpdate)

### [#](#Properties) Properties

- [priority](./ShareSystem.html#priority)
- [schema](./ShareSystem.html#schema)
- [EVENTS](./ShareSystem.html#EVENTS)

### [#](#Accessors) Accessors

- [el](./ShareSystem.html#el)
- [recordState](./ShareSystem.html#recordState)
- [scene](./ShareSystem.html#scene)
- [supported](./ShareSystem.html#supported)
- [version](./ShareSystem.html#version)

### [#](#Methods) Methods

- [captureToArrayBuffer](./ShareSystem.html#captureToArrayBuffer)
- [captureToArrayBufferAsync](./ShareSystem.html#captureToArrayBufferAsync)
- [captureToDataURL](./ShareSystem.html#captureToDataURL)
- [captureToDataURLAsync](./ShareSystem.html#captureToDataURLAsync)
- [captureToFriends](./ShareSystem.html#captureToFriends)
- [captureToLocalPath](./ShareSystem.html#captureToLocalPath)
- [getData](./ShareSystem.html#getData)
- [recordFinishToAlbum](./ShareSystem.html#recordFinishToAlbum)
- [recordFinishToTempFile](./ShareSystem.html#recordFinishToTempFile)
- [recordPause](./ShareSystem.html#recordPause)
- [recordResume](./ShareSystem.html#recordResume)
- [recordStart](./ShareSystem.html#recordStart)
- [setData](./ShareSystem.html#setData)
- [setDataOne](./ShareSystem.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new ShareSystem**()

#### [#](#Inherited-from) Inherited from

[Component](./Component.html).[constructor](./Component.html#constructor)

## [#](#Events-2) Events

### [#](#onAdd) onAdd

▸ **onAdd**(`parent`, `data`): `void`

所挂载的`element`被挂载到场景时触发的回调。

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `parent` | [`Element`](./Element.html) |
| `data` | [`IShareSystemData`](./../interfaces/IShareSystemData.html) |

#### [#](#Returns) Returns

`void`

#### [#](#Inherited-from-2) Inherited from

[Component](./Component.html).[onAdd](./Component.html#onAdd)

---

### [#](#onRelease) onRelease

▸ **onRelease**(`data`): `void`

从被挂载的`element`上被移除，或是`element`被销毁时，触发的回调。
一般用于释放持有的资源。

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `data` | [`IShareSystemData`](./../interfaces/IShareSystemData.html) |

#### [#](#Returns-2) Returns

`void`

#### [#](#Inherited-from-3) Inherited from

[Component](./Component.html).[onRelease](./Component.html#onRelease)

---

### [#](#onRemove) onRemove

▸ **onRemove**(`parent`, `data`): `void`

所挂载的`element`从父节点`parent`被移除时，或者自己从`element`上被移除时，触发的回调。
一般用于消除功能的运作。
**如果一个组件的元素直接被销毁了，那这个组件就不会经历onRemove而是直接进入onRelease。**

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `parent` | [`Element`](./Element.html) |
| `data` | [`IShareSystemData`](./../interfaces/IShareSystemData.html) |

#### [#](#Returns-3) Returns

`void`

#### [#](#Inherited-from-4) Inherited from

[Component](./Component.html).[onRemove](./Component.html#onRemove)

---

### [#](#onTick) onTick

▸ **onTick**(`deltaTime`, `data`): `void`

渲染每帧触发的回调。

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `deltaTime` | `number` |
| `data` | [`IShareSystemData`](./../interfaces/IShareSystemData.html) |

#### [#](#Returns-4) Returns

`void`

#### [#](#Inherited-from-5) Inherited from

[Component](./Component.html).[onTick](./Component.html#onTick)

---

### [#](#onUpdate) onUpdate

▸ **onUpdate**(`data`, `preData`): `void`

数据更新时触发的回调。

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `data` | [`IShareSystemData`](./../interfaces/IShareSystemData.html) |
| `preData` | [`IShareSystemData`](./../interfaces/IShareSystemData.html) |

#### [#](#Returns-5) Returns

`void`

#### [#](#Inherited-from-6) Inherited from

[Component](./Component.html).[onUpdate](./Component.html#onUpdate)

## [#](#Properties-2) Properties

### [#](#priority) priority

• `Readonly` **priority**: `number`

自定义组件的更新优先级。

#### [#](#Overrides) Overrides

[Component](./Component.html).[priority](./Component.html#priority)

---

### [#](#schema) schema

• `Readonly` **schema**: [`IComponentSchema`](./../interfaces/IComponentSchema.html) = `{}`

自定义组件的`schema`。

#### [#](#Inherited-from-7) Inherited from

[Component](./Component.html).[schema](./Component.html#schema)

---

### [#](#EVENTS) EVENTS

▪ `Static` **EVENTS**: `string`[] = `[]`

#### [#](#Inherited-from-8) Inherited from

[Component](./Component.html).[EVENTS](./Component.html#EVENTS)

## [#](#Accessors-2) Accessors

### [#](#el) el

• `get` **el**(): [`Element`](./Element.html)

挂载的元素。

#### [#](#Returns-6) Returns

[`Element`](./Element.html)

---

### [#](#recordState) recordState

• `get` **recordState**(): [`EShareRecordState`](./../enums/EShareRecordState.html)

当前录屏状态。

#### [#](#Returns-7) Returns

[`EShareRecordState`](./../enums/EShareRecordState.html)

---

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

当前场景。

#### [#](#Returns-8) Returns

[`Scene`](./Scene.html)

---

### [#](#supported) supported

• `get` **supported**(): `boolean`

当前是否支持分享系统。

#### [#](#Returns-9) Returns

`boolean`

---

### [#](#version) version

• `get` **version**(): `number`

当前版本，每次有数据更新都会增加，可以用作和其他组件合作的依据。

#### [#](#Returns-10) Returns

`number`

## [#](#Methods-2) Methods

### [#](#captureToArrayBuffer) captureToArrayBuffer

▸ **captureToArrayBuffer**(`options?`): `ArrayBuffer`

**`deprecated`** 请在`v3.0.2`后使用异步版本，同步版本不再维护，请使用`captureToArrayBufferAsync`。
截屏输出为`ArrayBuffer`。

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `options` | [`IShareCaptureOptions`](./../interfaces/IShareCaptureOptions.html) |

#### [#](#Returns-11) Returns

`ArrayBuffer`

---

### [#](#captureToArrayBufferAsync) captureToArrayBufferAsync

▸ **captureToArrayBufferAsync**(`options?`): `Promise`<`ArrayBuffer`>

截屏输出为`ArrayBuffer`。

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `options` | [`IShareCaptureOptions`](./../interfaces/IShareCaptureOptions.html) |

#### [#](#Returns-12) Returns

`Promise`<`ArrayBuffer`>

---

### [#](#captureToDataURL) captureToDataURL

▸ **captureToDataURL**(`options?`): `string`

**`deprecated`** 请在`v3.0.2`后使用异步版本，同步版本不再维护，请使用`captureToDataURLAsync`。
截屏输出为`base64`。

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `options` | [`IShareCaptureOptions`](./../interfaces/IShareCaptureOptions.html) |

#### [#](#Returns-13) Returns

`string`

---

### [#](#captureToDataURLAsync) captureToDataURLAsync

▸ **captureToDataURLAsync**(`options?`): `Promise`<`string`>

截屏输出为`base64`。

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `options` | [`IShareCaptureOptions`](./../interfaces/IShareCaptureOptions.html) |

#### [#](#Returns-14) Returns

`Promise`<`string`>

---

### [#](#captureToFriends) captureToFriends

▸ **captureToFriends**(`options?`): `Promise`<`void`>

直接截屏分享给好友。

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `options` | [`IShareCaptureOptions`](./../interfaces/IShareCaptureOptions.html) |

#### [#](#Returns-15) Returns

`Promise`<`void`>

---

### [#](#captureToLocalPath) captureToLocalPath

▸ **captureToLocalPath**(`options?`, `callback`): `Promise`<`void`>

截屏输出为本地路径，回调完成后会自动释放。

**`params`** callback 接受结果的回调，处理完后会释放文件。在v2.27.1前是异步，之后兼容同步和异步。

#### [#](#Parameters-11) Parameters

| Name | Type |
| --- | --- |
| `options` | [`IShareCaptureOptions`](./../interfaces/IShareCaptureOptions.html) |
| `callback` | (`fp`: `string`) => `void` | `Promise`<`void`> |

#### [#](#Returns-16) Returns

`Promise`<`void`>

---

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`IShareSystemData`](./../interfaces/IShareSystemData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends `never` |

#### [#](#Parameters-12) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-17) Returns

[`IShareSystemData`](./../interfaces/IShareSystemData.html)[`T`]

#### [#](#Inherited-from-9) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#recordFinishToAlbum) recordFinishToAlbum

▸ **recordFinishToAlbum**(): `Promise`<`void`>

录屏完成，直接保存到用户相册。

#### [#](#Returns-18) Returns

`Promise`<`void`>

---

### [#](#recordFinishToTempFile) recordFinishToTempFile

▸ **recordFinishToTempFile**(): `Promise`<`string`>

录屏完成，输出到临时文件。

#### [#](#Returns-19) Returns

`Promise`<`string`>

临时文件地址

---

### [#](#recordPause) recordPause

▸ **recordPause**(): `Promise`<`void`>

暂停本次录屏。

#### [#](#Returns-20) Returns

`Promise`<`void`>

---

### [#](#recordResume) recordResume

▸ **recordResume**(): `Promise`<`void`>

唤醒本次录屏。

#### [#](#Returns-21) Returns

`Promise`<`void`>

---

### [#](#recordStart) recordStart

▸ **recordStart**(`options?`): `Promise`<`void`>

启动录屏。

#### [#](#Parameters-13) Parameters

| Name | Type |
| --- | --- |
| `options?` | [`IShareRecordOptions`](./../interfaces/IShareRecordOptions.html) |

#### [#](#Returns-22) Returns

`Promise`<`void`>

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-14) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`IShareSystemData`](./../interfaces/IShareSystemData.html)> |

#### [#](#Returns-23) Returns

`void`

#### [#](#Inherited-from-10) Inherited from

[Component](./Component.html).[setData](./Component.html#setData)

---

### [#](#setDataOne) setDataOne

▸ **setDataOne**<`T`>(`key`, `value`): `void`

设置一个数据。

#### [#](#Type-parameters-2) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends `never` |

#### [#](#Parameters-15) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`IShareSystemData`](./../interfaces/IShareSystemData.html)[`T`] |

#### [#](#Returns-24) Returns

`void`

#### [#](#Inherited-from-11) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

Incorrect translation.