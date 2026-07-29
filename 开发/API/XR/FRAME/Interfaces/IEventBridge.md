[xr-frame](./../) / [Exports](./../modules.html) / IEventBridge

# [#](#Interface-IEventBridge) Interface: IEventBridge

## [#](#Table-of-contents) Table of contents

### [#](#Methods) Methods

- [bindEntitiesToBones](./IEventBridge.html#bindEntitiesToBones)
- [bindEntityToBone](./IEventBridge.html#bindEntityToBone)
- [entityAddChild](./IEventBridge.html#entityAddChild)
- [entityAddChildAtIndex](./IEventBridge.html#entityAddChildAtIndex)
- [entityClear](./IEventBridge.html#entityClear)
- [entityRemoveFromParent](./IEventBridge.html#entityRemoveFromParent)
- [entitySetActive](./IEventBridge.html#entitySetActive)
- [entitySetLocalMatrixDirty](./IEventBridge.html#entitySetLocalMatrixDirty)
- [refreshWorldTransform](./IEventBridge.html#refreshWorldTransform)
- [setRootEntity](./IEventBridge.html#setRootEntity)
- [unbindEntitiesFromBones](./IEventBridge.html#unbindEntitiesFromBones)
- [unbindEntityFromBone](./IEventBridge.html#unbindEntityFromBone)

## [#](#Methods-2) Methods

### [#](#bindEntitiesToBones) bindEntitiesToBones

▸ **bindEntitiesToBones**(`entities`, `boneEntities`): `void`

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `entities` | { `id`: `number` }[] |
| `boneEntities` | { `id`: `number` }[] |

#### [#](#Returns) Returns

`void`

---

### [#](#bindEntityToBone) bindEntityToBone

▸ **bindEntityToBone**(`entity`, `boneEntity`): `void`

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `entity` | `Object` |
| `entity.id` | `number` |
| `boneEntity` | `Object` |
| `boneEntity.id` | `number` |

#### [#](#Returns-2) Returns

`void`

---

### [#](#entityAddChild) entityAddChild

▸ **entityAddChild**(`entity`, `child`): `void`

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `entity` | `number` |
| `child` | `number` |

#### [#](#Returns-3) Returns

`void`

---

### [#](#entityAddChildAtIndex) entityAddChildAtIndex

▸ **entityAddChildAtIndex**(`entity`, `child`, `index`): `void`

#### [#](#Parameters-4) Parameters

| Name | Type |
| --- | --- |
| `entity` | `number` |
| `child` | `number` |
| `index` | `number` |

#### [#](#Returns-4) Returns

`void`

---

### [#](#entityClear) entityClear

▸ **entityClear**(`entity`): `void`

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `entity` | `number` |

#### [#](#Returns-5) Returns

`void`

---

### [#](#entityRemoveFromParent) entityRemoveFromParent

▸ **entityRemoveFromParent**(`entity`): `void`

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `entity` | `number` |

#### [#](#Returns-6) Returns

`void`

---

### [#](#entitySetActive) entitySetActive

▸ **entitySetActive**(`entity`, `active`): `void`

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `entity` | `number` |
| `active` | `boolean` |

#### [#](#Returns-7) Returns

`void`

---

### [#](#entitySetLocalMatrixDirty) entitySetLocalMatrixDirty

▸ **entitySetLocalMatrixDirty**(`entity`): `void`

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `entity` | `number` |

#### [#](#Returns-8) Returns

`void`

---

### [#](#refreshWorldTransform) refreshWorldTransform

▸ **refreshWorldTransform**(): `void`

#### [#](#Returns-9) Returns

`void`

---

### [#](#setRootEntity) setRootEntity

▸ **setRootEntity**(`entity`): `void`

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `entity` | `number` |

#### [#](#Returns-10) Returns

`void`

---

### [#](#unbindEntitiesFromBones) unbindEntitiesFromBones

▸ **unbindEntitiesFromBones**(`entities`): `void`

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `entities` | { `id`: `number` }[] |

#### [#](#Returns-11) Returns

`void`

---

### [#](#unbindEntityFromBone) unbindEntityFromBone

▸ **unbindEntityFromBone**(`entity`): `void`

#### [#](#Parameters-11) Parameters

| Name | Type |
| --- | --- |
| `entity` | `Object` |
| `entity.id` | `number` |

#### [#](#Returns-12) Returns

`void`

Incorrect translation.