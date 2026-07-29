[xr-frame](./../) / [Exports](./../modules.html) / Effect

# [#](#Class-Effect) Class: Effect

特效资源，定义了渲染所需的大部分参数，被[Material](./Material.html)所引用。

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./Effect.html#constructor)

### [#](#Properties) Properties

- [description](./Effect.html#description)

### [#](#Accessors) Accessors

- [name](./Effect.html#name)
- [passCount](./Effect.html#passCount)
- [scene](./Effect.html#scene)

### [#](#Methods) Methods

- [warmUp](./Effect.html#warmUp)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new Effect**(`_scene`, `description`)

根据特效配置生成特效资源。
**注意，不建议自己创建，请使用`scene.createEffect`。**

#### [#](#Parameters) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `_scene` | [`Scene`](./Scene.html) | - |
| `description` | [`IEffectAsset`](./../interfaces/IEffectAsset.html) | 配置。 |

## [#](#Properties-2) Properties

### [#](#description) description

• `Readonly` **description**: [`IEffectAsset`](./../interfaces/IEffectAsset.html)

## [#](#Accessors-2) Accessors

### [#](#name) name

• `get` **name**(): `string`

获取名称。

#### [#](#Returns) Returns

`string`

---

### [#](#passCount) passCount

• `get` **passCount**(): `number`

有几个Pass。

#### [#](#Returns-2) Returns

`number`

---

### [#](#scene) scene

• `get` **scene**(): [`Scene`](./Scene.html)

获取场景实例。

#### [#](#Returns-3) Returns

[`Scene`](./Scene.html)

## [#](#Methods-2) Methods

### [#](#warmUp) warmUp

▸ **warmUp**(): `boolean`

预编译

#### [#](#Returns-4) Returns

`boolean`

Incorrect translation.