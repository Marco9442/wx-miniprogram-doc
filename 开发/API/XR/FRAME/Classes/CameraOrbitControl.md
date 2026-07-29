[xr-frame](./../) / [Exports](./../modules.html) / CameraOrbitControl

# [#](#Class-CameraOrbitControl) Class: CameraOrbitControl

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`ICameraOrbitControlData`](./../interfaces/ICameraOrbitControlData.html)>

  ↳ **`CameraOrbitControl`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./CameraOrbitControl.html#constructor)

### [#](#Events) Events

- [onAdd](./CameraOrbitControl.html#onAdd)
- [onRelease](./CameraOrbitControl.html#onRelease)
- [onRemove](./CameraOrbitControl.html#onRemove)
- [onTick](./CameraOrbitControl.html#onTick)
- [onUpdate](./CameraOrbitControl.html#onUpdate)

### [#](#Properties) Properties

- [dampingFactor](./CameraOrbitControl.html#dampingFactor)
- [enableDamping](./CameraOrbitControl.html#enableDamping)
- [isEnabled](./CameraOrbitControl.html#isEnabled)
- [isLockMove](./CameraOrbitControl.html#isLockMove)
- [isLockRotate](./CameraOrbitControl.html#isLockRotate)
- [isLockX](./CameraOrbitControl.html#isLockX)
- [isLockY](./CameraOrbitControl.html#isLockY)
- [isLockZoom](./CameraOrbitControl.html#isLockZoom)
- [panMax](./CameraOrbitControl.html#panMax)
- [panMin](./CameraOrbitControl.html#panMin)
- [panSpeed](./CameraOrbitControl.html#panSpeed)
- [priority](./CameraOrbitControl.html#priority)
- [rotateSpeed](./CameraOrbitControl.html#rotateSpeed)
- [schema](./CameraOrbitControl.html#schema)
- [zoomMax](./CameraOrbitControl.html#zoomMax)
- [zoomMin](./CameraOrbitControl.html#zoomMin)
- [zoomSpeed](./CameraOrbitControl.html#zoomSpeed)
- [EVENTS](./CameraOrbitControl.html#EVENTS)

### [#](#Accessors) Accessors

- [damping](./CameraOrbitControl.html#damping)
- [el](./CameraOrbitControl.html#el)
- [scene](./CameraOrbitControl.html#scene)
- [target](./CameraOrbitControl.html#target)
- [version](./CameraOrbitControl.html#version)

### [#](#Methods) Methods

- [disable](./CameraOrbitControl.html#disable)
- [enable](./CameraOrbitControl.html#enable)
- [getData](./CameraOrbitControl.html#getData)
- [setData](./CameraOrbitControl.html#setData)
- [setDataOne](./CameraOrbitControl.html#setDataOne)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new CameraOrbitControl**()

#### [#](#Inherited-from) Inherited from

[Component](./Component.html).[constructor](./Component.html#constructor)

## [#](#Events-2) Events

### [#](#onAdd) onAdd

▸ **onAdd**(`parent`, `data`): `void`

添加到世界，继承请先`super.onAdd()`。

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `parent` | [`Element`](./Element.html) |
| `data` | [`ICameraOrbitControlData`](./../interfaces/ICameraOrbitControlData.html) |

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
| `data` | [`ICameraOrbitControlData`](./../interfaces/ICameraOrbitControlData.html) |

#### [#](#Returns-2) Returns

`void`

#### [#](#Inherited-from-3) Inherited from

[Component](./Component.html).[onRelease](./Component.html#onRelease)

---

### [#](#onRemove) onRemove

▸ **onRemove**(): `void`

销毁，继承请先`super.onUpdate()`。

#### [#](#Returns-3) Returns

`void`

#### [#](#Inherited-from-4) Inherited from

[Component](./Component.html).[onRemove](./Component.html#onRemove)

---

### [#](#onTick) onTick

▸ **onTick**(`deltaTime`, `data`): `void`

渲染每帧触发的回调。

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `deltaTime` | `number` |
| `data` | [`ICameraOrbitControlData`](./../interfaces/ICameraOrbitControlData.html) |

#### [#](#Returns-4) Returns

`void`

#### [#](#Inherited-from-5) Inherited from

[Component](./Component.html).[onTick](./Component.html#onTick)

---

### [#](#onUpdate) onUpdate

▸ **onUpdate**(`data`): `void`

每一帧更新，继承请先`super.onUpdate()`。

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `data` | [`ICameraOrbitControlData`](./../interfaces/ICameraOrbitControlData.html) |

#### [#](#Returns-5) Returns

`void`

#### [#](#Inherited-from-6) Inherited from

[Component](./Component.html).[onUpdate](./Component.html#onUpdate)

## [#](#Properties-2) Properties

### [#](#dampingFactor) dampingFactor

• **dampingFactor**: `number` = `0.1`

阻尼系数。

---

### [#](#enableDamping) enableDamping

• **enableDamping**: `boolean` = `true`

开启阻尼缓动。

---

### [#](#isEnabled) isEnabled

• **isEnabled**: `boolean` = `false`

是否已经开启。

---

### [#](#isLockMove) isLockMove

• **isLockMove**: `boolean` = `false`

是否锁定移动。

---

### [#](#isLockRotate) isLockRotate

• **isLockRotate**: `boolean` = `false`

是否锁定旋转。

---

### [#](#isLockX) isLockX

• **isLockX**: `boolean` = `false`

是否锁定横向旋转。

---

### [#](#isLockY) isLockY

• **isLockY**: `boolean` = `false`

是否锁定纵向旋转。

---

### [#](#isLockZoom) isLockZoom

• **isLockZoom**: `boolean` = `false`

是否锁定缩放。

---

### [#](#panMax) panMax

• **panMax**: [`Vector3`](./Vector3.html)

允许的最大平移边界。

---

### [#](#panMin) panMin

• **panMin**: [`Vector3`](./Vector3.html)

允许的最小平移边界。

---

### [#](#panSpeed) panSpeed

• **panSpeed**: `number` = `1`

平移速度。

---

### [#](#priority) priority

• `Readonly` **priority**: `number`

自定义组件的更新优先级。

#### [#](#Inherited-from-7) Inherited from

[Component](./Component.html).[priority](./Component.html#priority)

---

### [#](#rotateSpeed) rotateSpeed

• **rotateSpeed**: `number` = `1`

旋转速度。

---

### [#](#schema) schema

• `Readonly` **schema**: [`IComponentSchema`](./../interfaces/IComponentSchema.html)

详见[CameraOrbitControlSchema](./../modules.html#CameraOrbitControlSchema)。

#### [#](#Overrides) Overrides

[Component](./Component.html).[schema](./Component.html#schema)

---

### [#](#zoomMax) zoomMax

• **zoomMax**: `number`

允许的最大缩放值。

---

### [#](#zoomMin) zoomMin

• **zoomMin**: `number` = `-Infinity`

允许的最小缩放值。

---

### [#](#zoomSpeed) zoomSpeed

• **zoomSpeed**: `number` = `1`

缩放速度。

---

### [#](#EVENTS) EVENTS

▪ `Static` **EVENTS**: `string`[] = `[]`

#### [#](#Inherited-from-8) Inherited from

[Component](./Component.html).[EVENTS](./Component.html#EVENTS)

## [#](#Accessors-2) Accessors

### [#](#damping) damping

• `get` **damping**(): `boolean`

当前是否正在缓动。

#### [#](#Returns-6) Returns

`boolean`

---

### [#](#el) el

• `get` **el**(): [`Element`](./Element.html)

挂载的元素。

#### [#](#Returns-7) Returns

[`Element`](./Element.html)

---

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

当前场景。

#### [#](#Returns-8) Returns

[`Scene`](./Scene.html)

---

### [#](#target) target

• `get` **target**(): [`Vector3`](./Vector3.html)

获取当前目标。

#### [#](#Returns-9) Returns

[`Vector3`](./Vector3.html)

---

### [#](#version) version

• `get` **version**(): `number`

当前版本，每次有数据更新都会增加，可以用作和其他组件合作的依据。

#### [#](#Returns-10) Returns

`number`

## [#](#Methods-2) Methods

### [#](#disable) disable

▸ **disable**(): `void`

关闭控制器。

#### [#](#Returns-11) Returns

`void`

---

### [#](#enable) enable

▸ **enable**(): `void`

启动控制器。

#### [#](#Returns-12) Returns

`void`

---

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`ICameraOrbitControlData`](./../interfaces/ICameraOrbitControlData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`ICameraOrbitControlData`](./../interfaces/ICameraOrbitControlData.html) |

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-13) Returns

[`ICameraOrbitControlData`](./../interfaces/ICameraOrbitControlData.html)[`T`]

#### [#](#Inherited-from-9) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`ICameraOrbitControlData`](./../interfaces/ICameraOrbitControlData.html)> |

#### [#](#Returns-14) Returns

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
| `T` | extends keyof [`ICameraOrbitControlData`](./../interfaces/ICameraOrbitControlData.html) |

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`ICameraOrbitControlData`](./../interfaces/ICameraOrbitControlData.html)[`T`] |

#### [#](#Returns-15) Returns

`void`

#### [#](#Inherited-from-11) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

Incorrect translation.