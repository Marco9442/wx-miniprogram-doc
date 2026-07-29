XR-FRAME/Interfaces/IEnvData/
[xr-frame](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/) / [Exports](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/modules.html) / IEnvData
# [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IEnvData.html\#Interface-IEnvData) Interface: IEnvData
[Env](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/Env.html) 组件数据接口。
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IEnvData.html\#Table-of-contents) Table of contents
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IEnvData.html\#Properties) Properties
- [diffuseExp](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IEnvData.html#diffuseExp)
- [envData](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IEnvData.html#envData)
- [isSky2D](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IEnvData.html#isSky2D)
- [rotation](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IEnvData.html#rotation)
- [skyMap](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IEnvData.html#skyMap)
- [specularExp](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IEnvData.html#specularExp)
## [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IEnvData.html\#Properties-2) Properties
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IEnvData.html\#diffuseExp) diffuseExp
• \*\*diffuseExp\*\*: `number`
漫反射部分曝光。
`xml`中的数据类型为`number`，默认为`1`。
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IEnvData.html\#envData) envData
• `Optional` \*\*envData\*\*: [`EnvData`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/classes/EnvData.html)
要使用的环境数据资源。
`xml`中的数据类型为`env-data`资源。
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IEnvData.html\#isSky2D) isSky2D
• `Optional` \*\*isSky2D\*\*: `boolean`
是否用2D模式渲染天空盒，此时必须为`skyMap`必须 \*\*不\*\* 为`CubeTexture`。
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IEnvData.html\#rotation) rotation
• \*\*rotation\*\*: `number`
环境旋转角度。
`xml`中的数据类型为`number`，默认为`0`。
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IEnvData.html\#skyMap) skyMap
• `Optional` \*\*skyMap\*\*: `default` \| [`ITextureWrapper`](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/ITextureWrapper.html)
可以用于覆盖`envData`中的`skybox`。
`xml`中的数据类型为`texture`资源。
\* \* \*
### [\#](https://developers.weixin.qq.com/miniprogram/dev/api/xr-frame/interfaces/IEnvData.html\#specularExp) specularExp
• \*\*specularExp\*\*: `number`
镜面反射部分曝光。
`xml`中的数据类型为`number`，默认为`1`。