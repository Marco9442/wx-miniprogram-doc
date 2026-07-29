[xr-frame](./../) / [Exports](./../modules.html) / IEffectAsset

# [#](#Interface-IEffectAsset) Interface: IEffectAsset

`Effect`资源的参数接口。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [defaultRenderQueue](./IEffectAsset.html#defaultRenderQueue)
- [images](./IEffectAsset.html#images)
- [name](./IEffectAsset.html#name)
- [passes](./IEffectAsset.html#passes)
- [properties](./IEffectAsset.html#properties)
- [shaders](./IEffectAsset.html#shaders)

## [#](#Properties-2) Properties

### [#](#defaultRenderQueue) defaultRenderQueue

• **defaultRenderQueue**: `number`

使用该`Effect`的`Material`的默认渲染队列。
透明物体需要大于`2500`！

---

### [#](#images) images

• `Optional` **images**: { `default`: `string` ; `key`: `string` ; `macro?`: `string` }[]

纹理资源，传给UniformBlock的另一部分。

---

### [#](#name) name

• **name**: `string`

名字，应当和`registerEffect`时的名字一致。

---

### [#](#passes) passes

• **passes**: { `lightMode`: `string` ; `renderStates?`: [`IRenderStates`](./IRenderStates.html) ; `shaders`: [`number`, `number`] ; `useMaterialRenderStates`: `boolean` }[]

渲染时的`passes`，渲染时指定的`lightMode`的每个`pass`都会被按顺序绘制。

---

### [#](#properties) properties

• `Optional` **properties**: { `default`: `number`[] ; `key`: `string` ; `macro?`: `string` ; `num?`: `number` ; `type`: [`EUniformType`](./../enums/EUniformType.html) }[]

属性，传给UniformBlock的一部分。

---

### [#](#shaders) shaders

• **shaders**: `string`[]

所有的`shader`列表。

Incorrect translation.