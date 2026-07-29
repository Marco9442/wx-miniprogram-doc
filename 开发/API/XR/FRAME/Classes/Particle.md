[xr-frame](./../) / [Exports](./../modules.html) / Particle

# [#](#Class-Particle) Class: Particle

## [#](#Hierarchy) Hierarchy

- `BasicParticle`

  ↳ **`Particle`**

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Particle.html#constructor)

### [#](#Events) Events

- [onAdd](./Particle.html#onAdd)
- [onRelease](./Particle.html#onRelease)
- [onRemove](./Particle.html#onRemove)
- [onTick](./Particle.html#onTick)
- [onUpdate](./Particle.html#onUpdate)

### [#](#Properties) Properties

- [priority](./Particle.html#priority)
- [schema](./Particle.html#schema)
- [subEmitters](./Particle.html#subEmitters)
- [EVENTS](./Particle.html#EVENTS)

### [#](#Accessors) Accessors

- [billboardMode](./Particle.html#billboardMode)
- [data](./Particle.html#data)
- [el](./Particle.html#el)
- [emitterPosition](./Particle.html#emitterPosition)
- [id](./Particle.html#id)
- [material](./Particle.html#material)
- [particleEmitter](./Particle.html#particleEmitter)
- [scene](./Particle.html#scene)
- [spriteChangeSpeed](./Particle.html#spriteChangeSpeed)
- [useBillboard](./Particle.html#useBillboard)
- [useRampGradients](./Particle.html#useRampGradients)
- [useRandomSpriteCellIndex](./Particle.html#useRandomSpriteCellIndex)
- [useSpriteCellLoop](./Particle.html#useSpriteCellLoop)
- [useSpriteSheet](./Particle.html#useSpriteSheet)
- [version](./Particle.html#version)

### [#](#Methods) Methods

- [addAlphaGradient](./Particle.html#addAlphaGradient)
- [addColorGradient](./Particle.html#addColorGradient)
- [addColorRemapGradient](./Particle.html#addColorRemapGradient)
- [addDragGradient](./Particle.html#addDragGradient)
- [addLimitSpeedGradient](./Particle.html#addLimitSpeedGradient)
- [addRampGradient](./Particle.html#addRampGradient)
- [addSizeGradient](./Particle.html#addSizeGradient)
- [addSpeedScaleGradient](./Particle.html#addSpeedScaleGradient)
- [clone](./Particle.html#clone)
- [createBoxEmitter](./Particle.html#createBoxEmitter)
- [createPointEmitter](./Particle.html#createPointEmitter)
- [createSphereEmitter](./Particle.html#createSphereEmitter)
- [createSubEmitter](./Particle.html#createSubEmitter)
- [getData](./Particle.html#getData)
- [initParticle](./Particle.html#initParticle)
- [resetParticle](./Particle.html#resetParticle)
- [setData](./Particle.html#setData)
- [setDataOne](./Particle.html#setDataOne)
- [start](./Particle.html#start)
- [stop](./Particle.html#stop)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Particle**()

#### [#](#Inherited-from) Inherited from

BasicParticle.constructor

## [#](#Events-2) Events

### [#](#onAdd) onAdd

• **onAdd**:

---

### [#](#onRelease) onRelease

• **onRelease**:

---

### [#](#onRemove) onRemove

• **onRemove**:

---

### [#](#onTick) onTick

• **onTick**:

---

### [#](#onUpdate) onUpdate

• **onUpdate**:

## [#](#Properties-2) Properties

### [#](#priority) priority

• `Readonly` **priority**: `number` = `300`

#### [#](#Overrides) Overrides

BasicParticle.priority

---

### [#](#schema) schema

• `Readonly` **schema**: [`IComponentSchema`](./../interfaces/IComponentSchema.html)

详见[ParticleSchema](./../modules.html#ParticleSchema)。

#### [#](#Inherited-from-2) Inherited from

BasicParticle.schema

---

### [#](#subEmitters) subEmitters

• **subEmitters**: `any` = `null`

---

### [#](#EVENTS) EVENTS

▪ `Static` **EVENTS**: `string`[]

#### [#](#Overrides-2) Overrides

BasicParticle.EVENTS

## [#](#Accessors-2) Accessors

### [#](#billboardMode) billboardMode

• `get` **billboardMode**(): `number`

#### [#](#Returns) Returns

`number`

• `set` **billboardMode**(`value`): `void`

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `value` | `number` |

#### [#](#Returns-2) Returns

`void`

---

### [#](#data) data

• `get` **data**(): [`IParticleData`](./../interfaces/IParticleData.html)

#### [#](#Returns-3) Returns

[`IParticleData`](./../interfaces/IParticleData.html)

• `set` **data**(`value`): `void`

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `value` | [`IParticleData`](./../interfaces/IParticleData.html) |

#### [#](#Returns-4) Returns

`void`

---

### [#](#el) el

• `get` **el**(): [`Element`](./Element.html)

挂载的元素。

#### [#](#Returns-5) Returns

[`Element`](./Element.html)

---

### [#](#emitterPosition) emitterPosition

• `get` **emitterPosition**(): [`Vector3`](./Vector3.html)

#### [#](#Returns-6) Returns

[`Vector3`](./Vector3.html)

• `set` **emitterPosition**(`value`): `void`

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `value` | [`Vector3`](./Vector3.html) |

#### [#](#Returns-7) Returns

`void`

---

### [#](#id) id

• `get` **id**(): `number`

#### [#](#Returns-8) Returns

`number`

---

### [#](#material) material

• `get` **material**(): [`Material`](./Material.html)

#### [#](#Returns-9) Returns

[`Material`](./Material.html)

• `set` **material**(`value`): `void`

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `value` | [`Material`](./Material.html) |

#### [#](#Returns-10) Returns

`void`

---

### [#](#particleEmitter) particleEmitter

• `get` **particleEmitter**(): `BasicShapeEmitter`

#### [#](#Returns-11) Returns

`BasicShapeEmitter`

---

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

当前场景。

#### [#](#Returns-12) Returns

[`Scene`](./Scene.html)

---

### [#](#spriteChangeSpeed) spriteChangeSpeed

• `get` **spriteChangeSpeed**(): `number`

#### [#](#Returns-13) Returns

`number`

---

### [#](#useBillboard) useBillboard

• `get` **useBillboard**(): `boolean`

#### [#](#Returns-14) Returns

`boolean`

• `set` **useBillboard**(`value`): `void`

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `value` | `boolean` |

#### [#](#Returns-15) Returns

`void`

---

### [#](#useRampGradients) useRampGradients

• `get` **useRampGradients**(): `boolean`

#### [#](#Returns-16) Returns

`boolean`

• `set` **useRampGradients**(`value`): `void`

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `value` | `boolean` |

#### [#](#Returns-17) Returns

`void`

---

### [#](#useRandomSpriteCellIndex) useRandomSpriteCellIndex

• `get` **useRandomSpriteCellIndex**(): `boolean`

#### [#](#Returns-18) Returns

`boolean`

---

### [#](#useSpriteCellLoop) useSpriteCellLoop

• `get` **useSpriteCellLoop**(): `boolean`

#### [#](#Returns-19) Returns

`boolean`

---

### [#](#useSpriteSheet) useSpriteSheet

• `get` **useSpriteSheet**(): `boolean`

#### [#](#Returns-20) Returns

`boolean`

• `set` **useSpriteSheet**(`value`): `void`

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `value` | `boolean` |

#### [#](#Returns-21) Returns

`void`

---

### [#](#version) version

• `get` **version**(): `number`

当前版本，每次有数据更新都会增加，可以用作和其他组件合作的依据。

#### [#](#Returns-22) Returns

`number`

## [#](#Methods-2) Methods

### [#](#addAlphaGradient) addAlphaGradient

▸ **addAlphaGradient**(`gradient`, `alpha`, `alpha2?`): `void`

添加粒子运动过程中的透明度变化规则。

#### [#](#Parameters-8) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `gradient` | `number` | 指定所处粒子生命周期的阶段 |
| `alpha` | `number` | 指定粒子颜色透明度的左区间[0-1] |
| `alpha2?` | `number` | 指定粒子颜色透明度的右区间[0-1] |

#### [#](#Returns-23) Returns

`void`

#### [#](#Inherited-from-3) Inherited from

BasicParticle.addAlphaGradient

---

### [#](#addColorGradient) addColorGradient

▸ **addColorGradient**(`gradient`, `color1`, `color2?`): `void`

添加粒子运动过程中的颜色变化规则。

#### [#](#Parameters-9) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `gradient` | `number` | 指定所处粒子生命周期的阶段 |
| `color1` | [`Vector4`](./Vector4.html) | 指定粒子颜色的左区间 |
| `color2?` | [`Vector4`](./Vector4.html) | 指定粒子颜色的右区间 |

#### [#](#Returns-24) Returns

`void`

#### [#](#Inherited-from-4) Inherited from

BasicParticle.addColorGradient

---

### [#](#addColorRemapGradient) addColorRemapGradient

▸ **addColorRemapGradient**(`gradient`, `min`, `max?`): `void`

添加粒子运动过程中的透明度变化范围。

#### [#](#Parameters-10) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `gradient` | `number` | 指定所处粒子生命周期的阶段 |
| `min` | `number` | 指定粒子透明度值的左区间 |
| `max?` | `number` | 指定粒子透明度值的右区间 |

#### [#](#Returns-25) Returns

`void`

#### [#](#Inherited-from-5) Inherited from

BasicParticle.addColorRemapGradient

---

### [#](#addDragGradient) addDragGradient

▸ **addDragGradient**(`gradient`, `drag`, `drag2?`): `void`

添加粒子运动过程中的阻力规则。

#### [#](#Parameters-11) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `gradient` | `number` | 指定所处粒子生命周期的阶段 |
| `drag` | `number` | - |
| `drag2?` | `number` | - |

#### [#](#Returns-26) Returns

`void`

#### [#](#Inherited-from-6) Inherited from

BasicParticle.addDragGradient

---

### [#](#addLimitSpeedGradient) addLimitSpeedGradient

▸ **addLimitSpeedGradient**(`gradient`, `limitSpeed`, `limitSpeed2?`): `void`

添加粒子运动过程中的速度限制规则。

#### [#](#Parameters-12) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `gradient` | `number` | 指定所处粒子生命周期的阶段 |
| `limitSpeed` | `number` | 指定粒子限制速度的左区间 |
| `limitSpeed2?` | `number` | 指定粒子限制速度的右区间 |

#### [#](#Returns-27) Returns

`void`

#### [#](#Inherited-from-7) Inherited from

BasicParticle.addLimitSpeedGradient

---

### [#](#addRampGradient) addRampGradient

▸ **addRampGradient**(`gradient`, `color`): `void`

添加粒子运动过程中的根据透明度影响的颜色变化规则，将通过颜色变化图纹理进行采样。

#### [#](#Parameters-13) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `gradient` | `any` | 指定粒子颜色变化图的具体位置，对应具体值应为(1-alpha) |
| `color` | `any` | 指定该位置的颜色 |

#### [#](#Returns-28) Returns

`void`

#### [#](#Inherited-from-8) Inherited from

BasicParticle.addRampGradient

---

### [#](#addSizeGradient) addSizeGradient

▸ **addSizeGradient**(`gradient`, `size`, `size2?`): `void`

添加粒子运动过程中的尺寸变化规则。

#### [#](#Parameters-14) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `gradient` | `number` | 指定所处粒子生命周期的阶段 |
| `size` | `number` | 指定粒子尺寸的左区间 |
| `size2?` | `number` | 指定粒子尺寸的右区间 |

#### [#](#Returns-29) Returns

`void`

#### [#](#Inherited-from-9) Inherited from

BasicParticle.addSizeGradient

---

### [#](#addSpeedScaleGradient) addSpeedScaleGradient

▸ **addSpeedScaleGradient**(`gradient`, `speed`, `speed2?`): `void`

添加粒子运动过程中的速度变化规则。

#### [#](#Parameters-15) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `gradient` | `number` | 指定所处粒子生命周期的阶段 |
| `speed` | `number` | 指定粒子速度的左区间 |
| `speed2?` | `number` | 指定粒子速度的右区间 |

#### [#](#Returns-30) Returns

`void`

#### [#](#Inherited-from-10) Inherited from

BasicParticle.addSpeedScaleGradient

---

### [#](#clone) clone

▸ **clone**(): [`Particle`](./Particle.html)

获取一个拷贝的粒子系统。

#### [#](#Returns-31) Returns

[`Particle`](./Particle.html)

#### [#](#Inherited-from-11) Inherited from

BasicParticle.clone

---

### [#](#createBoxEmitter) createBoxEmitter

▸ **createBoxEmitter**(`direction1`, `direction2`, `minEmitBox`, `maxEmitBox`): `default`

创建一个箱形发射器。

#### [#](#Parameters-16) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `direction1` | [`Vector3`](./Vector3.html) | 粒子运动方向左区间 |
| `direction2` | [`Vector3`](./Vector3.html) | 粒子运动方向右区间 |
| `minEmitBox` | [`Vector3`](./Vector3.html) | 粒子生成位置最小允许坐标 |
| `maxEmitBox` | [`Vector3`](./Vector3.html) | 粒子生成位置最大允许坐标 |

#### [#](#Returns-32) Returns

`default`

箱形发射器

#### [#](#Inherited-from-12) Inherited from

BasicParticle.createBoxEmitter

---

### [#](#createPointEmitter) createPointEmitter

▸ **createPointEmitter**(`direction1`, `direction2`): `default`

创建一个点发射器。

#### [#](#Parameters-17) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `direction1` | [`Vector3`](./Vector3.html) | 粒子运动方向左区间 |
| `direction2` | [`Vector3`](./Vector3.html) | 粒子运动方向右区间 |

#### [#](#Returns-33) Returns

`default`

点发射器

#### [#](#Inherited-from-13) Inherited from

BasicParticle.createPointEmitter

---

### [#](#createSphereEmitter) createSphereEmitter

▸ **createSphereEmitter**(`radius`, `radiusRange`, `arc`, `randomizeDirection`): `default`

创建一个球形发射器。

#### [#](#Parameters-18) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `radius` | `number` | 球形半径 |
| `radiusRange` | `number` | 球形区域内的覆盖范围[0-1] |
| `arc` | `number` | 粒子在球形内生成的角度区间[0-360] |
| `randomizeDirection` | `number` | 粒子运动方向偏离程度[0-1] |

#### [#](#Returns-34) Returns

`default`

球形发射器

#### [#](#Inherited-from-14) Inherited from

BasicParticle.createSphereEmitter

---

### [#](#createSubEmitter) createSubEmitter

▸ **createSubEmitter**(`data`): `SubEmitter`

获取一个粒子子发射器。

#### [#](#Parameters-19) Parameters

| Name | Type |
| --- | --- |
| `data` | [`IParticleData`](./../interfaces/IParticleData.html) |

#### [#](#Returns-35) Returns

`SubEmitter`

#### [#](#Inherited-from-15) Inherited from

BasicParticle.createSubEmitter

---

### [#](#getData) getData

▸ **getData**<`T`>(`key`): [`IParticleData`](./../interfaces/IParticleData.html)[`T`]

获取一个当前值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IParticleData`](./../interfaces/IParticleData.html) |

#### [#](#Parameters-20) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |

#### [#](#Returns-36) Returns

[`IParticleData`](./../interfaces/IParticleData.html)[`T`]

#### [#](#Inherited-from-16) Inherited from

BasicParticle.getData

---

### [#](#initParticle) initParticle

▸ **initParticle**(`data`): `void`

初始化粒子系统的状态。

#### [#](#Parameters-21) Parameters

| Name | Type |
| --- | --- |
| `data` | [`IParticleData`](./../interfaces/IParticleData.html) |

#### [#](#Returns-37) Returns

`void`

---

### [#](#resetParticle) resetParticle

▸ **resetParticle**(): `void`

重置粒子系统的状态。

#### [#](#Returns-38) Returns

`void`

---

### [#](#setData) setData

▸ **setData**(`data`): `void`

不通过`xml`而是直接设置`data`，注意值的类型需要和`schema`中一致。

#### [#](#Parameters-22) Parameters

| Name | Type |
| --- | --- |
| `data` | `Partial`<[`IParticleData`](./../interfaces/IParticleData.html)> |

#### [#](#Returns-39) Returns

`void`

#### [#](#Inherited-from-17) Inherited from

BasicParticle.setData

---

### [#](#setDataOne) setDataOne

▸ **setDataOne**<`T`>(`key`, `value`): `void`

设置一个数据。

#### [#](#Type-parameters-2) Type parameters

| Name | Type |
| --- | --- |
| `T` | extends keyof [`IParticleData`](./../interfaces/IParticleData.html) |

#### [#](#Parameters-23) Parameters

| Name | Type |
| --- | --- |
| `key` | `T` |
| `value` | [`IParticleData`](./../interfaces/IParticleData.html)[`T`] |

#### [#](#Returns-40) Returns

`void`

#### [#](#Inherited-from-18) Inherited from

BasicParticle.setDataOne

---

### [#](#start) start

▸ **start**(`delay?`): `void`

粒子系统开始播放。

#### [#](#Parameters-24) Parameters

| Name | Type | Default value | Description |
| --- | --- | --- | --- |
| `delay` | `number` | `0` | 设定粒子延时几秒后再播放。 |

#### [#](#Returns-41) Returns

`void`

---

### [#](#stop) stop

▸ **stop**(): `void`

停止粒子系统与其子发射器的播放。

#### [#](#Returns-42) Returns

`void`

Incorrect translation.