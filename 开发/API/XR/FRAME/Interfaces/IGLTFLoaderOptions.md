[xr-frame](./../) / [Exports](./../modules.html) / IGLTFLoaderOptions

# [#](#Interface-IGLTFLoaderOptions) Interface: IGLTFLoaderOptions

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [ignoreError](./IGLTFLoaderOptions.html#ignoreError)
- [preserveRaw](./IGLTFLoaderOptions.html#preserveRaw)

## [#](#Properties-2) Properties

### [#](#ignoreError) ignoreError

• **ignoreError**: `number`[]

*(基础库2.31.1及之后)*
可以忽略xr-frame对GLTF模型的某一些限制，来强行渲染有问题的GLTF模型。
ErrorCode会在渲染模型失败后，由console报出。
填写-1则忽略所有限制。

---

### [#](#preserveRaw) preserveRaw

• **preserveRaw**: `boolean`

*(基础库2.32.1及之后)*
开启了之后会在GLTFModel中保留原始json。

Incorrect translation.