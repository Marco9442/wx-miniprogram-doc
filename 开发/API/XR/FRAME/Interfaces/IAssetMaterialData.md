[xr-frame](./../) / [Exports](./../modules.html) / IAssetMaterialData

# [#](#Interface-IAssetMaterialData) Interface: IAssetMaterialData

`AssetMaterial`数据接口。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [assetId](./IAssetMaterialData.html#assetId)
- [effect](./IAssetMaterialData.html#effect)
- [envData](./IAssetMaterialData.html#envData)
- [renderQueue](./IAssetMaterialData.html#renderQueue)
- [states](./IAssetMaterialData.html#states)
- [uniforms](./IAssetMaterialData.html#uniforms)

## [#](#Properties-2) Properties

### [#](#assetId) assetId

• **assetId**: `string`

被引用时的资源Id。
`xml`中的数据类型为`string`。

---

### [#](#effect) effect

• **effect**: [`Effect`](./../classes/Effect.html)

基于的效果。
`xml`中的数据类型为`effect`资源，默认为`simple`。

---

### [#](#envData) envData

• `Optional` **envData**: [`EnvData`](./../classes/EnvData.html)

用于覆盖全局的、材质维度的环境数据。

---

### [#](#renderQueue) renderQueue

• **renderQueue**: `number`

要覆盖的渲染顺序。
`xml`中的数据类型为`number`，无默认值。
大于等于`2500`视为透明物体。

---

### [#](#states) states

• **states**: [`string`, `string`][]

初始要写入的渲染状态`states`。
`xml`中的数据类型为`map`。
目前支持`renderQueue`、`cullOn`、`depthTestOn`、`depthTestWrite`、`alphaMode`、`alphaCutOff`。
`alphaMode`和`alphaCutOff`遵循glTF标准。

---

### [#](#uniforms) uniforms

• **uniforms**: [`string`, `string`][]

初始要写入的`uniforms`，类型根据`effect`中的定义决定。
`xml`中的数据类型为`map`。

Incorrect translation.