[xr-frame](./../) / [Exports](./../modules.html) / Animator

# [#](#Class-Animator) Class: Animator

## [#](#Hierarchy) Hierarchy

- [`Component`](./Component.html)<[`IAnimatorData`](./../interfaces/IAnimatorData.html)>

  ↳ **`Animator`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Animator.html#constructor)

### [#](#Events) Events

- [onAdd](./Animator.html#onAdd)
- [onRelease](./Animator.html#onRelease)
- [onRemove](./Animator.html#onRemove)
- [onTick](./Animator.html#onTick)
- [onUpdate](./Animator.html#onUpdate)

### [#](#Properties) Properties

- [priority](./Animator.html#priority)
- [schema](./Animator.html#schema)
- [EVENTS](./Animator.html#EVENTS)

### [#](#Accessors) Accessors

- [el](./Animator.html#el)
- [scene](./Animator.html#scene)
- [version](./Animator.html#version)

### [#](#Methods) Methods

- [addAnimation](./Animator.html#addAnimation)
- [createAnimation](./Animator.html#createAnimation)
- [getData](./Animator.html#getData)
- [pause](./Animator.html#pause)
- [pauseToFrame](./Animator.html#pauseToFrame)
- [play](./Animator.html#play)
- [removeAnimation](./Animator.html#removeAnimation)
- [resume](./Animator.html#resume)
- [setData](./Animator.html#setData)
- [setDataOne](./Animator.html#setDataOne)
- [stop](./Animator.html#stop)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Animator**()

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
| `data` | [`IAnimatorData`](./../interfaces/IAnimatorData.html) |

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
| `data` | [`IAnimatorData`](./../interfaces/IAnimatorData.html) |

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
| `data` | [`IAnimatorData`](./../interfaces/IAnimatorData.html) |

#### [#](#Returns-3) Returns

`void`

#### [#](#Inherited-from-4) Inherited from

[Component](./Component.html).[onRemove](./Component.html#onRemove)

---

### [#](#onTick) onTick

▸ **onTick**(`deltaTime`, `data`): `void`

渲染每帧触发的回调。

#### [#](#Parameters-4) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `deltaTime` | `number` | 单位为毫秒(ms)。 |
| `data` | [`IAnimatorData`](./../interfaces/IAnimatorData.html) | - |

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
| `data` | [`IAnimatorData`](./../interfaces/IAnimatorData.html) |
| `preData` | [`IAnimatorData`](./../interfaces/IAnimatorData.html) |

#### [#](#Returns-5) Returns

`void`

#### [#](#Inherited-from-6) Inherited from

[Component](./Component.html).[onUpdate](./Component.html#onUpdate)

## [#](#Properties-2) Properties

### [#](#priority) priority

• `Readonly` **priority**: `number` = `200`

自定义组件的更新优先级。

#### [#](#Overrides) Overrides

[Component](./Component.html).[priority](./Component.html#priority)

---

### [#](#schema) schema

• `Readonly` **schema**: [`IComponentSchema`](./../interfaces/IComponentSchema.html)

详见[AnimatorSchema](./../modules.html#AnimatorSchema)。

#### [#](#Overrides-2) Overrides

[Component](./Component.html).[schema](./Component.html#schema)

---

### [#](#EVENTS) EVENTS

▪ `Static` **EVENTS**: `string`[]

#### [#](#Overrides-3) Overrides

[Component](./Component.html).[EVENTS](./Component.html#EVENTS)

## [#](#Accessors-2) Accessors

### [#](#el) el

• `get` **el**(): [`Element`](./Element.html)

挂载的元素。

#### [#](#Returns-6) Returns

[`Element`](./Element.html)

---

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

当前场景。

#### [#](#Returns-7) Returns

[`Scene`](./Scene.html)

---

### [#](#version) version

• `get` **version**(): `number`

当前版本，每次有数据更新都会增加，可以用作和其他组件合作的依据。

#### [#](#Returns-8) Returns

`number`

## [#](#Methods-2) Methods

### [#](#addAnimation) addAnimation

▸ **addAnimation**<`T`>(`anim`, `clipMap?`): `T`

手动添加一个动画。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends [`Animation`](./Animation.html)<`any`, `any`, `T`> |

#### [#](#Parameters-6) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `anim` | `T` | - |
| `clipMap?` | `Object` | 可选的动画片段名字映射。 |

#### [#](#Returns-9) Returns

`T`

---

### [#](#createAnimation) createAnimation

▸ **createAnimation**<`T`>(`clz`, `data`, `clipMap?`): `T`

直接通过类`clz`和初始化数据`data`创建一个动画并添加到自身内。

#### [#](#Type-parameters-2) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends [`Animation`](./Animation.html)<`any`, `any`, `T`> |

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `clz` | (`scene`: [`Scene`](./Scene.html), `data`: `T`[`"__DATA_TYPE"`]) => `T` |
| `data` | `T`[`"__DATA_TYPE"`] |
| `clipMap?` | `Object` |

#### [#](#Returns-10) Returns

`T`

---

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`IAnimatorData`](./../interfaces/IAnimatorData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters-3) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IAnimatorData`](./../interfaces/IAnimatorData.html) |

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-11) Returns

[`IAnimatorData`](./../interfaces/IAnimatorData.html)[`T`]

#### [#](#Inherited-from-7) Inherited from

[Component](./Component.html).[getData](./Component.html#getData)

---

### [#](#pause) pause

▸ **pause**(`name?`): `void`

暂停播放。

#### [#](#Parameters-9) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `name?` | `string` | 需要暂停的片段，如果不填则暂停所有正在播放的片段。 |

#### [#](#Returns-12) Returns

`void`

---

### [#](#pauseToFrame) pauseToFrame

▸ **pauseToFrame**(`name`, `progress`): `void`

播放动画片段到某一进度并停下。

#### [#](#Parameters-10) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `name` | `string` | 片段名称。 |
| `progress` | `number` | 停到的某个进度，0~1。 |

#### [#](#Returns-13) Returns

`void`

---

### [#](#play) play

▸ **play**(`name`, `options?`): `void`

播放一个动画片段，**可以同时播放多个片段**。

#### [#](#Parameters-11) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `name` | `string` | 动画片段名称。 |
| `options?` | [`IAnimationPlayOptions`](./../interfaces/IAnimationPlayOptions.html) & { `[key: string]`: `any`; } | 播放选项。 |

#### [#](#Returns-14) Returns

`void`

---

### [#](#removeAnimation) removeAnimation

▸ **removeAnimation**(`anim`): `void`

移除一个动画

#### [#](#Parameters-12) Parameters

| Name | Type |
| --- | --- |
| `anim` | [`Animation`](./Animation.html)<`any`, `any`> |

#### [#](#Returns-15) Returns

`void`

---

### [#](#resume) resume

▸ **resume**(`name?`): `void`

唤醒暂停的动画。

#### [#](#Parameters-13) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `name?` | `string` | 需要唤醒的片段，如果不填则唤醒所有暂停的片段。 |

#### [#](#Returns-16) Returns

`void`

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-14) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`IAnimatorData`](./../interfaces/IAnimatorData.html)> |

#### [#](#Returns-17) Returns

`void`

#### [#](#Inherited-from-8) Inherited from

[Component](./Component.html).[setData](./Component.html#setData)

---

### [#](#setDataOne) setDataOne

▸ **setDataOne**<`T`>(`key`, `value`): `void`

设置一个数据。

#### [#](#Type-parameters-4) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IAnimatorData`](./../interfaces/IAnimatorData.html) |

#### [#](#Parameters-15) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`IAnimatorData`](./../interfaces/IAnimatorData.html)[`T`] |

#### [#](#Returns-18) Returns

`void`

#### [#](#Inherited-from-9) Inherited from

[Component](./Component.html).[setDataOne](./Component.html#setDataOne)

---

### [#](#stop) stop

▸ **stop**(`name?`): `void`

停止播放。

#### [#](#Parameters-16) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `name?` | `string` | 需要停止的片段，如果不填则停止所有正在播放的片段。 |

#### [#](#Returns-19) Returns

`void`

Incorrect translation.