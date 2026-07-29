[xr-frame](./../) / [Exports](./../modules.html) / IEnvDataOptions

# [#](#Interface-IEnvDataOptions) Interface: IEnvDataOptions

`EnvData`的参数接口。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [diffuse](./IEnvDataOptions.html#diffuse)
- [skybox](./IEnvDataOptions.html#skybox)
- [specular](./IEnvDataOptions.html#specular)

## [#](#Properties-2) Properties

### [#](#diffuse) diffuse

• `Optional` **diffuse**: `Object`

环境漫反射部分。

#### [#](#Type-declaration) Type declaration

| Name | Type | Description |
| --- | --- | --- |
| `coefficients` | `Float32Array` | 球谐系数SH9。 |

---

### [#](#skybox) skybox

• `Optional` **skybox**: `Object`

天空盒。

#### [#](#Type-declaration-2) Type declaration

| Name | Type | Description |
| --- | --- | --- |
| `half` | `boolean` | 是否只使用贴图的上半部分，一般在和`specular`共用贴图的时候为`true`。 |
| `map` | `default` | 贴图。 |

---

### [#](#specular) specular

• `Optional` **specular**: `Object`

环境高光反射部分。

#### [#](#Type-declaration-3) Type declaration

| Name | Type | Description |
| --- | --- | --- |
| `map` | `default` | 贴图。 |
| `mipmapCount?` | `number` | 使用的mipmap级数。 |
| `mipmaps` | `boolean` | 是否使用mipmap。 |
| `rgbd` | `boolean` | 是否使用`rgbd`编码来。 |
| `type` | `"2D"` | 贴图类型，目前只支持2D。 |

Incorrect translation.