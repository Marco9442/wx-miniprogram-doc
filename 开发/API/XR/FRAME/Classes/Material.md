[xr-frame](./../) / [Exports](./../modules.html) / Material

# [#](#Class-Material) Class: Material

材质资源，一般被代理到[XRMaterial](./XRMaterial.html)元素。

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Material.html#constructor)

### [#](#Accessors) Accessors

- [alphaCutOff](./Material.html#alphaCutOff)
- [alphaMode](./Material.html#alphaMode)
- [renderQueue](./Material.html#renderQueue)

### [#](#Methods) Methods

- [clearRenderState](./Material.html#clearRenderState)
- [clearRenderStates](./Material.html#clearRenderStates)
- [clone](./Material.html#clone)
- [getFloat](./Material.html#getFloat)
- [getMacro](./Material.html#getMacro)
- [getMatrix](./Material.html#getMatrix)
- [getRenderState](./Material.html#getRenderState)
- [getTexture](./Material.html#getTexture)
- [getVector](./Material.html#getVector)
- [initByEffect](./Material.html#initByEffect)
- [resetTexture](./Material.html#resetTexture)
- [setFloat](./Material.html#setFloat)
- [setMacro](./Material.html#setMacro)
- [setMacros](./Material.html#setMacros)
- [setMatrix](./Material.html#setMatrix)
- [setRenderState](./Material.html#setRenderState)
- [setRenderStates](./Material.html#setRenderStates)
- [setTexture](./Material.html#setTexture)
- [setTextureAsset](./Material.html#setTextureAsset)
- [setVector](./Material.html#setVector)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Material**(`_scene`)

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `_scene` | [`Scene`](./Scene.html) |

## [#](#Accessors-2) Accessors

### [#](#alphaCutOff) alphaCutOff

• `set` **alphaCutOff**(`value`): `void`

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `value` | `number` |

#### [#](#Returns) Returns

`void`

---

### [#](#alphaMode) alphaMode

• `set` **alphaMode**(`value`): `void`

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `value` | `"OPAQUE"` | `"BLEND"` | `"MASK"` |

#### [#](#Returns-2) Returns

`void`

---

### [#](#renderQueue) renderQueue

• `get` **renderQueue**(): `number`

透明物体需要大于`2500`！

#### [#](#Returns-3) Returns

`number`

• `set` **renderQueue**(`value`): `void`

透明物体需要大于`2500`！

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `value` | `number` |

#### [#](#Returns-4) Returns

`void`

## [#](#Methods-2) Methods

### [#](#clearRenderState) clearRenderState

▸ **clearRenderState**<`TKey`>(`key`): `boolean`

清除渲染状态。
清除材质的渲染状态，转而从effect中使用默认值。

#### [#](#Type-parameters) Type parameters

| Name | Type |
| --- | --- |
| `TKey` | extends keyof [`IRenderStates`](./../interfaces/IRenderStates.html) |

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `key` | `TKey` |

#### [#](#Returns-5) Returns

`boolean`

---

### [#](#clearRenderStates) clearRenderStates

▸ **clearRenderStates**(`states`): `boolean`

批量清除渲染状态。
清除材质的渲染状态，转而从effect中使用默认值。

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `states` | `Object` |

#### [#](#Returns-6) Returns

`boolean`

---

### [#](#clone) clone

▸ **clone**(): [`Material`](./Material.html)

拷贝自身，生成一份新的材质数据。

#### [#](#Returns-7) Returns

[`Material`](./Material.html)

---

### [#](#getFloat) getFloat

▸ **getFloat**(`key`): `number`

获取一个Float

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `key` | `string` |

#### [#](#Returns-8) Returns

`number`

---

### [#](#getMacro) getMacro

▸ **getMacro**(`key`): `boolean`

获取宏。

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `key` | `string` |

#### [#](#Returns-9) Returns

`boolean`

---

### [#](#getMatrix) getMatrix

▸ **getMatrix**(`key`): [`Matrix3`](./Matrix3.html) | [`Matrix4`](./Matrix4.html)

获取一个Vector值的拷贝。

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `key` | `string` |

#### [#](#Returns-10) Returns

[`Matrix3`](./Matrix3.html) | [`Matrix4`](./Matrix4.html)

---

### [#](#getRenderState) getRenderState

▸ **getRenderState**(`key`): `number` | `boolean`

获取渲染状态。

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `key` | `string` |

#### [#](#Returns-11) Returns

`number` | `boolean`

---

### [#](#getTexture) getTexture

▸ **getTexture**(`key`): `default`

获取材质中已设置的贴图。

#### [#](#Parameters-11) Parameters

| Name | Type |
| --- | --- |
| `key` | `string` |

#### [#](#Returns-12) Returns

`default`

---

### [#](#getVector) getVector

▸ **getVector**(`key`): [`Vector3`](./Vector3.html) | [`Vector2`](./Vector2.html) | [`Vector4`](./Vector4.html)

获取一个Vector值的拷贝。

#### [#](#Parameters-12) Parameters

| Name | Type |
| --- | --- |
| `key` | `string` |

#### [#](#Returns-13) Returns

[`Vector3`](./Vector3.html) | [`Vector2`](./Vector2.html) | [`Vector4`](./Vector4.html)

---

### [#](#initByEffect) initByEffect

▸ **initByEffect**(`effect`, `defaultUniforms?`): `void`

通过效果初始化材质。

#### [#](#Parameters-13) Parameters

| Name | Type |
| --- | --- |
| `effect` | [`Effect`](./Effect.html) |
| `defaultUniforms?` | `Object` |

#### [#](#Returns-14) Returns

`void`

---

### [#](#resetTexture) resetTexture

▸ **resetTexture**(`key`): `default`

#### [#](#Parameters-14) Parameters

| Name | Type |
| --- | --- |
| `key` | `string` |

#### [#](#Returns-15) Returns

`default`

---

### [#](#setFloat) setFloat

▸ **setFloat**(`key`, `value`): `boolean`

设置一个Float

#### [#](#Parameters-15) Parameters

| Name | Type |
| --- | --- |
| `key` | `string` |
| `value` | `number` |

#### [#](#Returns-16) Returns

`boolean`

是否设置成功

---

### [#](#setMacro) setMacro

▸ **setMacro**(`key`, `value`): `void`

设置宏。

#### [#](#Parameters-16) Parameters

| Name | Type |
| --- | --- |
| `key` | `string` |
| `value` | `number` | `boolean` |

#### [#](#Returns-17) Returns

`void`

---

### [#](#setMacros) setMacros

▸ **setMacros**(`marcos`): `void`

批量设置宏。

#### [#](#Parameters-17) Parameters

| Name | Type |
| --- | --- |
| `marcos` | `Object` |

#### [#](#Returns-18) Returns

`void`

---

### [#](#setMatrix) setMatrix

▸ **setMatrix**(`key`, `value`): `boolean`

设置一个Matrix

#### [#](#Parameters-18) Parameters

| Name | Type |
| --- | --- |
| `key` | `string` |
| `value` | [`Matrix3`](./Matrix3.html) | [`Matrix4`](./Matrix4.html) |

#### [#](#Returns-19) Returns

`boolean`

是否设置成功

---

### [#](#setRenderState) setRenderState

▸ **setRenderState**<`TKey`>(`key`, `value`): `boolean`

设置渲染状态。
只有标记了`useMaterialRenderStates`的Pass会受到影响

#### [#](#Type-parameters-2) Type parameters

| Name | Type |
| --- | --- |
| `TKey` | extends keyof [`IRenderStates`](./../interfaces/IRenderStates.html) |

#### [#](#Parameters-19) Parameters

| Name | Type |
| --- | --- |
| `key` | `TKey` |
| `value` | [`IRenderStates`](./../interfaces/IRenderStates.html)[`TKey`] |

#### [#](#Returns-20) Returns

`boolean`

---

### [#](#setRenderStates) setRenderStates

▸ **setRenderStates**(`states`): `boolean`

批量设置渲染状态。
只有标记了`useMaterialRenderStates`的Pass会受到影响。

#### [#](#Parameters-20) Parameters

| Name | Type |
| --- | --- |
| `states` | [`IRenderStates`](./../interfaces/IRenderStates.html) |

#### [#](#Returns-21) Returns

`boolean`

---

### [#](#setTexture) setTexture

▸ **setTexture**(`key`, `value`): `boolean`

设置一张贴图。

#### [#](#Parameters-21) Parameters

| Name | Type |
| --- | --- |
| `key` | `string` |
| `value` | `default` |

#### [#](#Returns-22) Returns

`boolean`

是否设置成功。

---

### [#](#setTextureAsset) setTextureAsset

▸ **setTextureAsset**(`key`, `assetId`): `boolean`

设置一张贴图。

#### [#](#Parameters-22) Parameters

| Name | Type |
| --- | --- |
| `key` | `string` |
| `assetId` | `string` |

#### [#](#Returns-23) Returns

`boolean`

是否设置成功。

---

### [#](#setVector) setVector

▸ **setVector**(`key`, `value`): `boolean`

设置一个Vector。

#### [#](#Parameters-23) Parameters

| Name | Type |
| --- | --- |
| `key` | `string` |
| `value` | [`Vector3`](./Vector3.html) | [`Vector2`](./Vector2.html) | [`Vector4`](./Vector4.html) |

#### [#](#Returns-24) Returns

`boolean`

是否设置成功。

Incorrect translation.