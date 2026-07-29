[xr-frame](./../) / [Exports](./../modules.html) / IEngineSettings

# [#](#Interface-IEngineSettings) Interface: IEngineSettings

index.ts

**`author`** : hikaridai(hikaridai@tencent.com)

**`date`** : 2020/8/18 下午4:48:36

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [alpha](./IEngineSettings.html#alpha)
- [audio](./IEngineSettings.html#audio)
- [backupURLs](./IEngineSettings.html#backupURLs)
- [baseURL](./IEngineSettings.html#baseURL)
- [cacheDelimiter](./IEngineSettings.html#cacheDelimiter)
- [cacheSizeLimit](./IEngineSettings.html#cacheSizeLimit)
- [designHeight](./IEngineSettings.html#designHeight)
- [designWidth](./IEngineSettings.html#designWidth)
- [fixedDeltaTime](./IEngineSettings.html#fixedDeltaTime)
- [gfxIgnoreAssert](./IEngineSettings.html#gfxIgnoreAssert)
- [globalHTTPRetry](./IEngineSettings.html#globalHTTPRetry)
- [gravity](./IEngineSettings.html#gravity)
- [logFilter](./IEngineSettings.html#logFilter)
- [logLevel](./IEngineSettings.html#logLevel)
- [mainScreenMSAA](./IEngineSettings.html#mainScreenMSAA)
- [physics3DLayerCollisionMatrix](./IEngineSettings.html#physics3DLayerCollisionMatrix)
- [profileGfx](./IEngineSettings.html#profileGfx)
- [realSizeLimit](./IEngineSettings.html#realSizeLimit)
- [renderHeight](./IEngineSettings.html#renderHeight)
- [renderWidth](./IEngineSettings.html#renderWidth)
- [shaderGlobalProperties](./IEngineSettings.html#shaderGlobalProperties)
- [useEngineSubcontext](./IEngineSettings.html#useEngineSubcontext)
- [workerPath](./IEngineSettings.html#workerPath)
- [workerTimeout](./IEngineSettings.html#workerTimeout)

## [#](#Properties-2) Properties

### [#](#alpha) alpha

• `Optional` **alpha**: `boolean`

是否开启透明通道输出

---

### [#](#audio) audio

• `Optional` **audio**: `Object`

音频全局定义

#### [#](#Type-declaration) Type declaration

| Name | Type | Description |
| --- | --- | --- |
| `globalVolume?` | `number` | 全局音量 |
| `maxRealVoices?` | `number` | 真实音频数量上限 |

---

### [#](#backupURLs) backupURLs

• **backupURLs**: `string`[]

如果baseURL找不到并且重试次数`globalHTTPRetry`大于0，则会依次尝试使用

---

### [#](#baseURL) baseURL

• **baseURL**: `string`

loader下载文件的默认根路径

---

### [#](#cacheDelimiter) cacheDelimiter

• **cacheDelimiter**: `string`

拼缓存的文件名的

---

### [#](#cacheSizeLimit) cacheSizeLimit

• **cacheSizeLimit**: `number`

最大缓存极限

---

### [#](#designHeight) designHeight

• **designHeight**: `number`

设计分辨率高

---

### [#](#designWidth) designWidth

• **designWidth**: `number`

设计分辨率宽

---

### [#](#fixedDeltaTime) fixedDeltaTime

• **fixedDeltaTime**: `number`

物理引擎的模拟步进固定间隔

---

### [#](#gfxIgnoreAssert) gfxIgnoreAssert

• **gfxIgnoreAssert**: `boolean`

---

### [#](#globalHTTPRetry) globalHTTPRetry

• **globalHTTPRetry**: `string`

全局loader下载文件重试次数

---

### [#](#gravity) gravity

• **gravity**: `number`

物理引擎的重力

---

### [#](#logFilter) logFilter

• **logFilter**: `boolean`

log过滤器

---

### [#](#logLevel) logLevel

• **logLevel**: `string`

log等级

---

### [#](#mainScreenMSAA) mainScreenMSAA

• **mainScreenMSAA**: `boolean`

是否开启MSAA

---

### [#](#physics3DLayerCollisionMatrix) physics3DLayerCollisionMatrix

• **physics3DLayerCollisionMatrix**: `string`

物理碰撞矩阵，以十六进制字符串表示

---

### [#](#profileGfx) profileGfx

• **profileGfx**: `string`

---

### [#](#realSizeLimit) realSizeLimit

• **realSizeLimit**: `number`

是否开启MSAA

---

### [#](#renderHeight) renderHeight

• **renderHeight**: `number`

渲染分辨率高

---

### [#](#renderWidth) renderWidth

• **renderWidth**: `number`

渲染分辨率宽

---

### [#](#shaderGlobalProperties) shaderGlobalProperties

• **shaderGlobalProperties**: { `default`: `string` | `number` | `number`[] ; `key`: `string` ; `type`: `"Float"` | `"Vector2"` | `"Vector3"` | `"Vector4"` | `"Matrix4"` | `"Texture"` }[]

全局Uniform定义

---

### [#](#useEngineSubcontext) useEngineSubcontext

• **useEngineSubcontext**: `boolean`

---

### [#](#workerPath) workerPath

• **workerPath**: `string`

自动生成的worker文件入口路径

---

### [#](#workerTimeout) workerTimeout

• **workerTimeout**: `number`

worker执行任务超时时间

Incorrect translation.