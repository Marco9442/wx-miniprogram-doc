## [#](#Type-aliases) Type aliases

### [#](#RaycastDesc) RaycastDesc

Ƭ **RaycastDesc**: `Object`

raycast函数的参数。

**`field`** origin 射线起点。

**`field`** unitDir 射线方向（单位向量）。

**`field`** distance 射线的最大长度。

**`field`** hit 用来接收碰撞信息的容器。

**`field`** layerMask 可以用来屏蔽一些物体。

**`field`** （未实现）queryTriggerInteraction，是否能与Trigger相交（默认能）。

#### [#](#Type-declaration) Type declaration

| Name | Type |
| --- | --- |
| `distance?` | `number` |
| `hit?` | [`RaycastHit`](./classes/RaycastHit.html) |
| `layerMask?` | `number` |
| `origin` | [`Vector3`](./classes/Vector3.html) |
| `unitDir` | [`Vector3`](./classes/Vector3.html) |

---

### [#](#TCameraBackground) TCameraBackground

Ƭ **TCameraBackground**: `"default"` | `"skybox"` | `"ar"`

相机背景渲染模式。

`default`模式只执行默认清屏。
`skybox`模式配合[Env](./classes/Env.html)组件使用。
`ar`模式配合[ARSystem](./classes/ARSystem.html)使用。

---

### [#](#TDirection) TDirection

Ƭ **TDirection**: `"forwards"` | `"backwards"` | `"both"`

动画播放的方向，如果是`both`，则会在`loop`开启时的每次循环中自动反转。

---

### [#](#TEventCallback) TEventCallback

Ƭ **TEventCallback**<`TParams`>: (`params`: `TParams`, `sender`: `Element`) => `void`

#### [#](#Type-parameters) Type parameters

| Name |
| --- |
| `TParams` |

#### [#](#Type-declaration-2) Type declaration

▸ (`params`, `sender`): `void`

事件管理器的回调。

##### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `params` | `TParams` |
| `sender` | `Element` |

##### [#](#Returns) Returns

`void`

---

### [#](#TTrackMode) TTrackMode

Ƭ **TTrackMode**: `"Plane"` | `"Marker"` | `"OSD"` | `"Face"` | `"Hand"` | `"Body"` | `"threeDof"`

[ARSystem](./classes/ARSystem.html)和[ARTracker](./classes/ARTracker.html)的跟踪模式。
其中`threeDof`需要基础库`2.30.4`以上支持。

---

### [#](#Texture) Texture

Ƭ **Texture**: `Kanata.Texture`

---

### [#](#UniformBlock) UniformBlock

Ƭ **UniformBlock**: `Kanata.UniformBlock`

---

### [#](#UniformDescriptor) UniformDescriptor

Ƭ **UniformDescriptor**: `Kanata.UniformDescriptor`

---

### [#](#VertexLayout) VertexLayout

Ƭ **VertexLayout**: `Kanata.VertexLayout`

## [#](#Variables) Variables

### [#](#ARSystemSchema) ARSystemSchema

• **ARSystemSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html)

[ARSystem](./classes/ARSystem.html)的`schema`，详见[IARSystemData](./interfaces/IARSystemData.html)。

---

### [#](#ARTrackSchema) ARTrackSchema

• **ARTrackSchema**: `Object`

[ARTracker](./classes/ARTracker.html)的`schema`，详见[IARTrackerData](./interfaces/IARTrackerData.html)。

#### [#](#Type-declaration-3) Type declaration

| Name | Type |
| --- | --- |
| `autoSync` | { `type`: `string` = 'number-array' } |
| `autoSync.type` | `string` |
| `image` | { `type`: `string` = 'image' } |
| `image.type` | `string` |
| `mode` | { `type`: `string` = 'string' } |
| `mode.type` | `string` |
| `src` | { `type`: `string` = 'string' } |
| `src.type` | `string` |

---

### [#](#ARTrackerDataMapping) ARTrackerDataMapping

• **ARTrackerDataMapping**: { `auto-sync`: `string`[] ; `hit-id`: `string`[] ; `image`: `string`[] ; `mode`: `string`[] ; `src`: `string`[] } & { `layer`: `string`[] ; `node-id`: `string`[] ; `position`: `string`[] ; `rotation`: `string`[] ; `scale`: `string`[] ; `visible`: `string`[] } & { `[key: string]`: `string`[]; }

默认包含[XRNode](./classes/XRNode.html)的所有属性映射，以及将[ARTracker](./classes/ARTracker.html)组件的属性进行映射。

---

### [#](#ARTrackerDefaultComponents) ARTrackerDefaultComponents

• **ARTrackerDefaultComponents**: [`IEntityComponents`](./interfaces/IEntityComponents.html)

默认包含[XRNode](./classes/XRNode.html)的所有默认组件，以及[ARTracker](./classes/ARTracker.html)组件。

---

### [#](#AnimatorSchema) AnimatorSchema

• **AnimatorSchema**: `Object`

[Animator](./classes/Animator.html)的`schema`定义。

**`see`** 解析后的接口详见 [IAnimatorData](./interfaces/IAnimatorData.html)

#### [#](#Type-declaration-4) Type declaration

| Name | Type |
| --- | --- |
| `autoPlay` | { `type`: `string` = 'dict' } |
| `autoPlay.type` | `string` |
| `clipMap` | { `type`: `string` = 'dict' } |
| `clipMap.type` | `string` |
| `keyframe` | { `type`: `string` = 'keyframe' } |
| `keyframe.type` | `string` |

---

### [#](#AssetLoadDataMapping) AssetLoadDataMapping

• **AssetLoadDataMapping**: { `asset-id`: `string`[] ; `defer`: `string`[] ; `options`: `string`[] ; `src`: `string`[] ; `type`: `string`[] } & { `[key: string]`: `string`[]; }

将[AssetLoad](./classes/AssetLoad.html)组件的属性进行映射。

---

### [#](#AssetLoadSchema) AssetLoadSchema

• **AssetLoadSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html)

[AssetLoad](./classes/AssetLoad.html)的`schema`，详见{@link IAssetLoadData}。

---

### [#](#AssetMaterialDataMapping) AssetMaterialDataMapping

• **AssetMaterialDataMapping**: { `asset-id`: `string`[] ; `effect`: `string`[] ; `env-data`: `string`[] ; `marcos`: `string`[] ; `render-queue`: `string`[] ; `states`: `string`[] ; `uniforms`: `string`[] } & { `[key: string]`: `string`[]; }

将[AssetMaterial](./classes/AssetMaterial.html)的属性进行映射。

---

### [#](#AssetMaterialDefaultComponents) AssetMaterialDefaultComponents

• **AssetMaterialDefaultComponents**: [`IEntityComponents`](./interfaces/IEntityComponents.html)

---

### [#](#AssetMaterialSchema) AssetMaterialSchema

• **AssetMaterialSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html)

[AssetMaterial](./classes/AssetMaterial.html)的`schema`，详见[IAssetMaterialData](./interfaces/IAssetMaterialData.html)。

---

### [#](#AssetPostProcessDataMapping) AssetPostProcessDataMapping

• **AssetPostProcessDataMapping**: { `asset-id`: `string`[] ; `data`: `string`[] ; `is-hdr`: `string`[] ; `type`: `string`[] } & { `[key: string]`: `string`[]; }

将[AssetPostProcess](./classes/AssetPostProcess.html)的属性进行映射。

---

### [#](#AssetPostProcessDefaultComponents) AssetPostProcessDefaultComponents

• **AssetPostProcessDefaultComponents**: [`IEntityComponents`](./interfaces/IEntityComponents.html)

---

### [#](#AssetRenderTextureDataMapping) AssetRenderTextureDataMapping

• **AssetRenderTextureDataMapping**: { `asset-id`: `string`[] ; `height`: `string`[] ; `is-hdr`: `string`[] ; `width`: `string`[] } & { `[key: string]`: `string`[]; }

将[AssetRenderTexture](./classes/AssetRenderTexture.html)的属性进行映射。

---

### [#](#AssetRenderTextureDefaultComponents) AssetRenderTextureDefaultComponents

• **AssetRenderTextureDefaultComponents**: [`IEntityComponents`](./interfaces/IEntityComponents.html)

---

### [#](#AssetRenderTextureSchema) AssetRenderTextureSchema

• **AssetRenderTextureSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html)

[AssetRenderTexture](./classes/AssetRenderTexture.html)的`schema`，详见[IAssetRenderTextureData](./interfaces/IAssetRenderTextureData.html)。

---

### [#](#AssetsDefaultComponents) AssetsDefaultComponents

• **AssetsDefaultComponents**: [`IEntityComponents`](./interfaces/IEntityComponents.html)

默认包含[Assets](./classes/Assets.html)组件。

---

### [#](#AssetsSchema) AssetsSchema

• **AssetsSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html) = `{}`

---

### [#](#BasicDataMapping) BasicDataMapping

• **BasicDataMapping**: `Object`

空的默认组件映射。

#### [#](#Index-signature) Index signature

▪ [key: `string`]: `string`[]

---

### [#](#BasicDefaultComponents) BasicDefaultComponents

• **BasicDefaultComponents**: [`IEntityComponents`](./interfaces/IEntityComponents.html) = `{}`

空的默认组件集。

---

### [#](#CameraDataMapping) CameraDataMapping

• **CameraDataMapping**: { `allow-features`: `string`[] ; `background`: `string`[] ; `clear-color`: `string`[] ; `clear-depth`: `string`[] ; `clear-stencil`: `string`[] ; `cull-mask`: `string`[] ; `depth`: `string`[] ; `far`: `string`[] ; `fov`: `string`[] ; `is-ar-camera`: `string`[] ; `is-clear-color`: `string`[] ; `is-clear-depth`: `string`[] ; `is-clear-stencil`: `string`[] ; `is-perspective`: `string`[] ; `near`: `string`[] ; `orth-size`: `string`[] ; `post-process`: `string`[] ; `render-target`: `string`[] ; `target`: `string`[] } & { `layer`: `string`[] ; `node-id`: `string`[] ; `position`: `string`[] ; `rotation`: `string`[] ; `scale`: `string`[] ; `visible`: `string`[] } & { `[key: string]`: `string`[]; }

默认包含[XRNode](./classes/XRNode.html)的所有属性映射，以及将[Camera](./classes/Camera.html)组件的属性进行映射。

---

### [#](#CameraDefaultComponents) CameraDefaultComponents

• **CameraDefaultComponents**: [`IEntityComponents`](./interfaces/IEntityComponents.html)

默认包含[XRNode](./classes/XRNode.html)的所有默认组件，以及[Camera](./classes/Camera.html)组件。

---

### [#](#CameraOrbitControlSchema) CameraOrbitControlSchema

• **CameraOrbitControlSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html)

[CameraOrbitControl](./classes/CameraOrbitControl.html)的`schema`，详见[ICameraOrbitControlData](./interfaces/ICameraOrbitControlData.html)。

---

### [#](#CameraSchema) CameraSchema

• **CameraSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html)

[Camera](./classes/Camera.html)的`schema`，详见[ICameraData](./interfaces/ICameraData.html)。

---

### [#](#CapsuleShapeSchema) CapsuleShapeSchema

• **CapsuleShapeSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html)

---

### [#](#CubeShapeSchema) CubeShapeSchema

• **CubeShapeSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html)

---

### [#](#EnvDataMapping) EnvDataMapping

• **EnvDataMapping**: { `diffuse-exp`: `string`[] ; `env-data`: `string`[] ; `is-sky2d`: `string`[] ; `rotation`: `string`[] ; `sky-map`: `string`[] ; `specular-exp`: `string`[] } & { `[key: string]`: `string`[]; }

默认将[Env](./classes/Env.html)组件的属性进行映射。

---

### [#](#EnvDefaultComponents) EnvDefaultComponents

• **EnvDefaultComponents**: [`IEntityComponents`](./interfaces/IEntityComponents.html)

默认包含[Env](./classes/Env.html)组件。

---

### [#](#EnvSchema) EnvSchema

• **EnvSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html)

[Env](./classes/Env.html)的`schema`，详见[IEnvData](./interfaces/IEnvData.html)。

---

### [#](#GLTFDataMapping) GLTFDataMapping

• **GLTFDataMapping**: { `cast-shadow`: `string`[] ; `model`: `string`[] ; `never-cull`: `string`[] ; `receive-shadow`: `string`[] ; `states`: `string`[] } & { `layer`: `string`[] ; `node-id`: `string`[] ; `position`: `string`[] ; `rotation`: `string`[] ; `scale`: `string`[] ; `visible`: `string`[] } & { `[key: string]`: `string`[]; }

默认包含[XRNode](./classes/XRNode.html)的所有属性映射，以及将[GLTF](./classes/GLTF.html)组件的属性进行映射。

- model → {@link IGLTFComponentData.model}
- cast-shadow → {@link IGLTFComponentData.castShadow}
- receive-shadow → {@link IGLTFComponentData.receiveShadow}

---

### [#](#GLTFDefaultComponents) GLTFDefaultComponents

• **GLTFDefaultComponents**: [`IEntityComponents`](./interfaces/IEntityComponents.html)

默认包含[XRNode](./classes/XRNode.html)的所有默认组件，以及[GLTF](./classes/GLTF.html)组件。

---

### [#](#GLTFSchema) GLTFSchema

• **GLTFSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html)

---

### [#](#LightDataMapping) LightDataMapping

• **LightDataMapping**: { `cast-shadow`: `string`[] ; `color`: `string`[] ; `inner-cone-angle`: `string`[] ; `intensity`: `string`[] ; `outer-cone-angle`: `string`[] ; `range`: `string`[] ; `shadow-bias`: `string`[] ; `shadow-distance`: `string`[] ; `shadow-strength`: `string`[] ; `type`: `string`[] } & { `layer`: `string`[] ; `node-id`: `string`[] ; `position`: `string`[] ; `rotation`: `string`[] ; `scale`: `string`[] ; `visible`: `string`[] } & { `[key: string]`: `string`[]; }

默认包含[XRNode](./classes/XRNode.html)的所有属性映射，以及将[Light](./classes/Light.html)组件的属性进行映射。

---

### [#](#LightDefaultComponents) LightDefaultComponents

• **LightDefaultComponents**: [`IEntityComponents`](./interfaces/IEntityComponents.html)

默认包含[XRNode](./classes/XRNode.html)的所有默认组件，以及[Light](./classes/Light.html)组件。

---

### [#](#LightSchema) LightSchema

• **LightSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html)

[Light](./classes/Light.html)的`schema`，详见[ILightData](./interfaces/ILightData.html)。

---

### [#](#MeshDataMapping) MeshDataMapping

• **MeshDataMapping**: { `cast-shadow`: `string`[] ; `env-data`: `string`[] ; `geometry`: `string`[] ; `material`: `string`[] ; `never-cull`: `string`[] ; `receive-shadow`: `string`[] ; `states`: `string`[] ; `uniforms`: `string`[] } & { `layer`: `string`[] ; `node-id`: `string`[] ; `position`: `string`[] ; `rotation`: `string`[] ; `scale`: `string`[] ; `visible`: `string`[] } & { `[key: string]`: `string`[]; }

默认包含[XRNode](./classes/XRNode.html)的所有属性映射，以及将[Mesh](./classes/Mesh.html)组件的属性进行映射。

---

### [#](#MeshDefaultComponents) MeshDefaultComponents

• **MeshDefaultComponents**: [`IEntityComponents`](./interfaces/IEntityComponents.html)

默认包含[XRNode](./classes/XRNode.html)的所有默认组件，以及[Mesh](./classes/Mesh.html)组件。

---

### [#](#MeshSchema) MeshSchema

• **MeshSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html)

[Mesh](./classes/Mesh.html)的`schema`，详见[IMeshData](./interfaces/IMeshData.html)。

---

### [#](#MeshShapeSchema) MeshShapeSchema

• **MeshShapeSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html)

---

### [#](#NodeDataMapping) NodeDataMapping

• **NodeDataMapping**: { `layer`: `string`[] ; `node-id`: `string`[] ; `position`: `string`[] ; `rotation`: `string`[] ; `scale`: `string`[] ; `visible`: `string`[] } & { `[key: string]`: `string`[]; }

默认将[Transform](./classes/Transform.html)组件的属性进行映射。

---

### [#](#NodeDefaultComponents) NodeDefaultComponents

• **NodeDefaultComponents**: [`IEntityComponents`](./interfaces/IEntityComponents.html)

默认包含[Transform](./classes/Transform.html)组件。

---

### [#](#ParticleDataMapping) ParticleDataMapping

• **ParticleDataMapping**: `Object`

#### [#](#Index-signature-2) Index signature

▪ [key: `string`]: `string`[]

---

### [#](#ParticleDefaultComponents) ParticleDefaultComponents

• **ParticleDefaultComponents**: [`IEntityComponents`](./interfaces/IEntityComponents.html)

---

### [#](#ParticleSchema) ParticleSchema

• **ParticleSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html)

[Particle](./classes/Particle.html)的`schema`定义。

**`see`** 解析后的接口详见 [IParticleData](./interfaces/IParticleData.html)

---

### [#](#RenderSystemSchema) RenderSystemSchema

• **RenderSystemSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html)

[RenderSystem](./classes/RenderSystem.html)的`schema`，详见[IRenderSystemData](./interfaces/IRenderSystemData.html)。

---

### [#](#RigidbodySchema) RigidbodySchema

• **RigidbodySchema**: `Object`

#### [#](#Type-declaration-5) Type declaration

| Name | Type |
| --- | --- |
| `constraintsMask` | { `type`: `string` = 'number' } |
| `constraintsMask.type` | `string` |
| `disabled` | { `type`: `string` = 'boolean' } |
| `disabled.type` | `string` |
| `kinematic` | { `type`: `string` = 'boolean' } |
| `kinematic.type` | `string` |
| `mass` | { `type`: `string` = 'number' } |
| `mass.type` | `string` |
| `useGravity` | { `type`: `string` = 'boolean' } |
| `useGravity.type` | `string` |

---

### [#](#SceneDataMapping) SceneDataMapping

• **SceneDataMapping**: `Object` = `{}`

场景的默认映射。

#### [#](#Index-signature-3) Index signature

▪ [key: `string`]: `string`[]

---

### [#](#SceneDefaultComponents) SceneDefaultComponents

• **SceneDefaultComponents**: [`IEntityComponents`](./interfaces/IEntityComponents.html)

场景的默认组件，均为系统。

---

### [#](#ShadowDataMapping) ShadowDataMapping

• **ShadowDataMapping**: { `layer`: `string`[] ; `node-id`: `string`[] ; `position`: `string`[] ; `rotation`: `string`[] ; `scale`: `string`[] ; `visible`: `string`[] } & { `[key: string]`: `string`[]; }

默认包含[XRNode](./classes/XRNode.html)的所有属性映射。

---

### [#](#ShadowDefaultComponents) ShadowDefaultComponents

• **ShadowDefaultComponents**: [`IEntityComponents`](./interfaces/IEntityComponents.html)

默认包含[XRNode](./classes/XRNode.html)的所有默认组件。

---

### [#](#ShapeInteractSchema) ShapeInteractSchema

• **ShapeInteractSchema**: `Object`

#### [#](#Type-declaration-6) Type declaration

| Name | Type |
| --- | --- |
| `bounciness` | { `type`: `string` = 'number' } |
| `bounciness.type` | `string` |
| `collide` | { `type`: `string` = 'boolean' } |
| `collide.type` | `string` |
| `disabled` | { `type`: `string` = 'boolean' } |
| `disabled.type` | `string` |
| `dynamicFriction` | { `type`: `string` = 'number' } |
| `dynamicFriction.type` | `string` |
| `staticFriction` | { `type`: `string` = 'number' } |
| `staticFriction.type` | `string` |

---

### [#](#SphereShapeSchema) SphereShapeSchema

• **SphereShapeSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html)

---

### [#](#TextDataMapping) TextDataMapping

• **TextDataMapping**: `Object`

#### [#](#Index-signature-4) Index signature

▪ [key: `string`]: `string`[]

---

### [#](#TextDefaultComponents) TextDefaultComponents

• **TextDefaultComponents**: [`IEntityComponents`](./interfaces/IEntityComponents.html)

---

### [#](#TextSchema) TextSchema

• **TextSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html)

---

### [#](#TransformSchema) TransformSchema

• **TransformSchema**: [`IComponentSchema`](./interfaces/IComponentSchema.html)

[Transform](./classes/Transform.html)的`schema`，详见[ITransformData](./interfaces/ITransformData.html)。

---

### [#](#noneParamsEaseFuncs) noneParamsEaseFuncs

• **noneParamsEaseFuncs**: `Object`

不需要自定义参数的一些内置插值曲线。

#### [#](#Type-declaration-7) Type declaration

| Name | Type |
| --- | --- |
| `ease-in` | (`x`: `number`) => `number` |
| `ease-in-back` | (`x`: `any`) => `number` |
| `ease-in-bounce` | (`x`: `any`) => `number` |
| `ease-in-circ` | (`x`: `any`) => `number` |
| `ease-in-cubic` | (`x`: `any`) => `number` |
| `ease-in-elastic` | (`x`: `any`) => `number` |
| `ease-in-expo` | (`x`: `any`) => `number` |
| `ease-in-out` | (`x`: `number`) => `number` |
| `ease-in-out-back` | (`x`: `any`) => `number` |
| `ease-in-out-bounce` | (`x`: `any`) => `number` |
| `ease-in-out-circ` | (`x`: `any`) => `number` |
| `ease-in-out-cubic` | (`x`: `any`) => `number` |
| `ease-in-out-elastic` | (`x`: `any`) => `number` |
| `ease-in-out-expo` | (`x`: `any`) => `number` |
| `ease-in-out-quad` | (`x`: `any`) => `number` |
| `ease-in-out-quart` | (`x`: `any`) => `number` |
| `ease-in-out-quint` | (`x`: `any`) => `number` |
| `ease-in-out-sine` | (`x`: `any`) => `number` |
| `ease-in-quad` | (`x`: `any`) => `number` |
| `ease-in-quart` | (`x`: `any`) => `number` |
| `ease-in-quint` | (`x`: `any`) => `number` |
| `ease-in-sine` | (`x`: `any`) => `number` |
| `ease-out` | (`x`: `number`) => `number` |
| `ease-out-back` | (`x`: `any`) => `number` |
| `ease-out-bounce` | `TEaseFunction` |
| `ease-out-circ` | (`x`: `any`) => `number` |
| `ease-out-cubic` | (`x`: `any`) => `number` |
| `ease-out-elastic` | (`x`: `any`) => `number` |
| `ease-out-expo` | (`x`: `any`) => `number` |
| `ease-out-quad` | (`x`: `any`) => `number` |
| `ease-out-quart` | (`x`: `any`) => `number` |
| `ease-out-quint` | (`x`: `any`) => `number` |
| `ease-out-sine` | (`x`: `any`) => `number` |
| `linear` | (`x`: `any`) => `any` |

---

### [#](#useParamsEaseFuncs) useParamsEaseFuncs

• **useParamsEaseFuncs**: `Object`

可以自定义参数的插值函数。

#### [#](#Type-declaration-8) Type declaration

| Name | Type |
| --- | --- |
| `cubic-bezier` | (`times`: `number`[], `params`: `number`[]) => (`x`: `number`) => `number` |
| `steps` | (`times`: `number`[], `params`: `number`[]) => (`x`: `number`) => `number` |

## [#](#Functions) Functions

### [#](#genLspMeta) genLspMeta

▸ **genLspMeta**(`scene`): `IXRFrameMeta`

#### [#](#Parameters-2) Parameters

| Name | Type |
| --- | --- |
| `scene` | [`Scene`](./classes/Scene.html) |

#### [#](#Returns-2) Returns

`IXRFrameMeta`

---

### [#](#isTextureWrapper) isTextureWrapper

▸ **isTextureWrapper**(`value`): value is ITextureWrapper

#### [#](#Parameters-3) Parameters

| Name | Type |
| --- | --- |
| `value` | `any` |

#### [#](#Returns-3) Returns

value is ITextureWrapper

---

### [#](#registerAssetLoader) registerAssetLoader

▸ **registerAssetLoader**(`type`, `clz`): `void`

注册一个资源加载器。注意注册后该`type`会被自动注册到DataValue中：[registerDataValue](./modules.html#registerDataValue)。
在基础库版本**v2.29.2**以上导出。

#### [#](#Parameters-4) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `type` | `string` | 类型，也是写在[AssetLoad](./classes/AssetLoad.html)上的那个`type`。 |
| `clz` | (`scene`: [`Scene`](./classes/Scene.html), `type`: `string`) => [`AssetLoader`](./classes/AssetLoader.html)<`any`, `any`> | 继承自[AssetLoader](./classes/AssetLoader.html)的自定义资源加载器类。 |

#### [#](#Returns-4) Returns

`void`

---

### [#](#registerComponent) registerComponent

▸ **registerComponent**(`type`, `clz`): `void`

向系统中注册一个组件，然后可以在`xml`中使用。

#### [#](#Parameters-5) Parameters

| Name | Type |
| --- | --- |
| `type` | `string` |
| `clz` | () => [`Component`](./classes/Component.html)<`any`> |

#### [#](#Returns-5) Returns

`void`

---

### [#](#registerDataValue) registerDataValue

▸ **registerDataValue**<`TDataValue`>(`type`, `handler`): `void`

为组件在`xml`中写的属性值按类型注册解析器，由于`xml`传入的值全部都是字符串，所以需要解析，比如：

```
registerDataValue('number', {create: (value: string, defaultValue: any, scene: Scene) => {
  return value === undefined ? defaultValue : parseFloat(value));
}});
```

就是注册了`number`类型，后续在组件的`schema`中写的`number`类型数据，就会走这个解析器。
**注意最后一个参数`scene`可以用于获取资源等，比如`scene.assets.getAssetWithState(type, value, defaultValue)`。** **如果是被资源加载器加载的资源，则会在资源加载器注册时自动注册数据类型，详见[AssetLoader](./classes/AssetLoader.html)**。

已经注册的类型可见[组件数据解析](../../../dev/component/xr-frame/core/data-values)。

#### [#](#Type-parameters-2) Type parameters

| Name |
| --- |
| `TDataValue` |

#### [#](#Parameters-6) Parameters

| Name | Type |
| --- | --- |
| `type` | `string` |
| `handler` | [`IDataValueHandler`](./interfaces/IDataValueHandler.html)<`TDataValue`> |

#### [#](#Returns-6) Returns

`void`

---

### [#](#registerEffect) registerEffect

▸ `Const` **registerEffect**(`id`, `factory`): `void`

注册`Effect`资源。

#### [#](#Parameters-7) Parameters

| Name | Type |
| --- | --- |
| `id` | `string` |
| `factory` | (`scene`: [`Scene`](./classes/Scene.html)) => [`Effect`](./classes/Effect.html) |

#### [#](#Returns-7) Returns

`void`

---

### [#](#registerElement) registerElement

▸ **registerElement**(`type`, `clz`): `void`

注册一个自定义元素。
注意注册的`type`在`xml`中使用时需要加上`xr-`前缀，比如注册`custom`类型的元素，使用时需要时`xr-custom`。

#### [#](#Parameters-8) Parameters

| Name | Type |
| --- | --- |
| `type` | `string` |
| `clz` | typeof [`Element`](./classes/Element.html) |

#### [#](#Returns-8) Returns

`void`

---

### [#](#registerGeometry) registerGeometry

▸ `Const` **registerGeometry**(`id`, `factory`): `void`

注册`Geometry`资源。

#### [#](#Parameters-9) Parameters

| Name | Type |
| --- | --- |
| `id` | `string` |
| `factory` | (`scene`: [`Scene`](./classes/Scene.html)) => [`Geometry`](./classes/Geometry.html) |

#### [#](#Returns-9) Returns

`void`

---

### [#](#registerMaterial) registerMaterial

▸ `Const` **registerMaterial**(`id`, `factory`): `void`

注册`Material`资源。

#### [#](#Parameters-10) Parameters

| Name | Type |
| --- | --- |
| `id` | `string` |
| `factory` | (`scene`: [`Scene`](./classes/Scene.html)) => [`Material`](./classes/Material.html) |

#### [#](#Returns-10) Returns

`void`

---

### [#](#registerTexture) registerTexture

▸ `Const` **registerTexture**(`id`, `factory`): `void`

注册`Texture`资源。

#### [#](#Parameters-11) Parameters

| Name | Type |
| --- | --- |
| `id` | `string` |
| `factory` | (`scene`: [`Scene`](./classes/Scene.html)) => `default` |

#### [#](#Returns-11) Returns

`void`

---

### [#](#registerUniformDesc) registerUniformDesc

▸ `Const` **registerUniformDesc**(`id`, `factory`): `void`

注册`UniformDescriptor`资源。

#### [#](#Parameters-12) Parameters

| Name | Type |
| --- | --- |
| `id` | `string` |
| `factory` | (`scene`: [`Scene`](./classes/Scene.html)) => `default` |

#### [#](#Returns-12) Returns

`void`

---

### [#](#registerVertexDataDesc) registerVertexDataDesc

▸ `Const` **registerVertexDataDesc**(`id`, `factory`): `void`

注册`VertexDataDescriptor`资源。

#### [#](#Parameters-13) Parameters

| Name | Type |
| --- | --- |
| `id` | `string` |
| `factory` | (`scene`: [`Scene`](./classes/Scene.html)) => `default` |

#### [#](#Returns-13) Returns

`void`

---

### [#](#registerVertexLayout) registerVertexLayout

▸ `Const` **registerVertexLayout**(`id`, `factory`): `void`

注册`VertexLayout`资源。

#### [#](#Parameters-14) Parameters

| Name | Type |
| --- | --- |
| `id` | `string` |
| `factory` | (`scene`: [`Scene`](./classes/Scene.html)) => `default` |

#### [#](#Returns-14) Returns

`void`

Incorrect translation.