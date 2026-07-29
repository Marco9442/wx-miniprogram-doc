[xr-frame](./../) / [Exports](./../modules.html) / IParticleData

# [#](#Interface-IParticleData) Interface: IParticleData

[Particle](./../classes/Particle.html)组件数据接口。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [angle](./IParticleData.html#angle)
- [angularSpeed](./IParticleData.html#angularSpeed)
- [atlas](./IParticleData.html#atlas)
- [atlasFrames](./IParticleData.html#atlasFrames)
- [atlasLoop](./IParticleData.html#atlasLoop)
- [atlasRandom](./IParticleData.html#atlasRandom)
- [atlasSpeed](./IParticleData.html#atlasSpeed)
- [burstCount](./IParticleData.html#burstCount)
- [burstCycle](./IParticleData.html#burstCycle)
- [burstInterval](./IParticleData.html#burstInterval)
- [burstTime](./IParticleData.html#burstTime)
- [capacity](./IParticleData.html#capacity)
- [colorChange](./IParticleData.html#colorChange)
- [delay](./IParticleData.html#delay)
- [emitRate](./IParticleData.html#emitRate)
- [emitterProps](./IParticleData.html#emitterProps)
- [emitterType](./IParticleData.html#emitterType)
- [endColor](./IParticleData.html#endColor)
- [gravity](./IParticleData.html#gravity)
- [lifeTime](./IParticleData.html#lifeTime)
- [mesh](./IParticleData.html#mesh)
- [neverCull](./IParticleData.html#neverCull)
- [prewarmCycles](./IParticleData.html#prewarmCycles)
- [renderMode](./IParticleData.html#renderMode)
- [scaleX](./IParticleData.html#scaleX)
- [scaleY](./IParticleData.html#scaleY)
- [size](./IParticleData.html#size)
- [sizeChange](./IParticleData.html#sizeChange)
- [speed](./IParticleData.html#speed)
- [speedChange](./IParticleData.html#speedChange)
- [speedDampen](./IParticleData.html#speedDampen)
- [startColor](./IParticleData.html#startColor)
- [startColor2](./IParticleData.html#startColor2)
- [states](./IParticleData.html#states)
- [stopDuration](./IParticleData.html#stopDuration)
- [texture](./IParticleData.html#texture)
- [uniforms](./IParticleData.html#uniforms)

## [#](#Properties-2) Properties

### [#](#angle) angle

• `Optional` **angle**: `number`[]

初始角度。

---

### [#](#angularSpeed) angularSpeed

• `Optional` **angularSpeed**: `number`[]

角速度。

---

### [#](#atlas) atlas

• `Optional` **atlas**: [`Atlas`](./../classes/Atlas.html)

动画图集信息。

---

### [#](#atlasFrames) atlasFrames

• `Optional` **atlasFrames**: `string`[]

指定图集帧名。

---

### [#](#atlasLoop) atlasLoop

• `Optional` **atlasLoop**: `boolean`

是否循环播放图集。

---

### [#](#atlasRandom) atlasRandom

• `Optional` **atlasRandom**: `boolean`

是否随机播放图集。

---

### [#](#atlasSpeed) atlasSpeed

• `Optional` **atlasSpeed**: `number`

图集切换速度。

---

### [#](#burstCount) burstCount

• `Optional` **burstCount**: `number`

---

### [#](#burstCycle) burstCycle

• `Optional` **burstCycle**: `number`

---

### [#](#burstInterval) burstInterval

• `Optional` **burstInterval**: `number`

---

### [#](#burstTime) burstTime

• `Optional` **burstTime**: `number`

---

### [#](#capacity) capacity

• `Optional` **capacity**: `number`

最大粒子数目。

---

### [#](#colorChange) colorChange

• `Optional` **colorChange**: [`string`, `string`][]

---

### [#](#delay) delay

• `Optional` **delay**: `number`

粒子系统启动延时秒数。

---

### [#](#emitRate) emitRate

• `Optional` **emitRate**: `number`

每秒粒子发射数。

---

### [#](#emitterProps) emitterProps

• `Optional` **emitterProps**: [`string`, `string`][]

发射器属性配置。

---

### [#](#emitterType) emitterType

• `Optional` **emitterType**: `string`

发射器类型。

---

### [#](#endColor) endColor

• `Optional` **endColor**: `number`[]

粒子结束时颜色。

---

### [#](#gravity) gravity

• `Optional` **gravity**: `number`

y轴方向上的每秒位移。

---

### [#](#lifeTime) lifeTime

• `Optional` **lifeTime**: `number`[]

生命周期时长。

---

### [#](#mesh) mesh

• `Optional` **mesh**: [`Geometry`](./../classes/Geometry.html)

网格信息。

---

### [#](#neverCull) neverCull

• `Optional` **neverCull**: `boolean`

---

### [#](#prewarmCycles) prewarmCycles

• `Optional` **prewarmCycles**: `number`

粒子预渲染周期数。

---

### [#](#renderMode) renderMode

• `Optional` **renderMode**: `string`

渲染模式。

---

### [#](#scaleX) scaleX

• `Optional` **scaleX**: `number`[]

粒子在x轴方向上的大小尺度。

---

### [#](#scaleY) scaleY

• `Optional` **scaleY**: `number`[]

粒子在y轴方向上的大小尺度。

---

### [#](#size) size

• `Optional` **size**: `number`[]

初始大小。

---

### [#](#sizeChange) sizeChange

• `Optional` **sizeChange**: [`string`, `string`][]

---

### [#](#speed) speed

• `Optional` **speed**: `number`[]

速度。

---

### [#](#speedChange) speedChange

• `Optional` **speedChange**: [`string`, `string`][]

---

### [#](#speedDampen) speedDampen

• `Optional` **speedDampen**: `number`

速度阻尼系数。

---

### [#](#startColor) startColor

• `Optional` **startColor**: `number`[]

粒子初始颜色左区间。

---

### [#](#startColor2) startColor2

• `Optional` **startColor2**: `number`[]

粒子初始颜色右区间。

---

### [#](#states) states

• `Optional` **states**: [`string`, `string`][]

---

### [#](#stopDuration) stopDuration

• `Optional` **stopDuration**: `number`

粒子系统生命周期时长。

---

### [#](#texture) texture

• `Optional` **texture**: `default`

纹理信息。

---

### [#](#uniforms) uniforms

• `Optional` **uniforms**: [`string`, `string`][]

Incorrect translation.