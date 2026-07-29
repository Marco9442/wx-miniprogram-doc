[xr-frame](./../) / [Exports](./../modules.html) / VideoTexture

# [#](#Class-VideoTexture) Class: VideoTexture

视频纹理。

## [#](#Table-of-contents) Table of contents

### [#](#Constructors) Constructors

- [constructor](./VideoTexture.html#constructor)

### [#](#Properties) Properties

- [onEnd](./VideoTexture.html#onEnd)

### [#](#Accessors) Accessors

- [autoPause](./VideoTexture.html#autoPause)
- [height](./VideoTexture.html#height)
- [state](./VideoTexture.html#state)
- [texture](./VideoTexture.html#texture)
- [width](./VideoTexture.html#width)

### [#](#Methods) Methods

- [pause](./VideoTexture.html#pause)
- [play](./VideoTexture.html#play)
- [release](./VideoTexture.html#release)
- [resume](./VideoTexture.html#resume)
- [seek](./VideoTexture.html#seek)
- [stop](./VideoTexture.html#stop)

## [#](#Constructors-2) Constructors

### [#](#constructor) constructor

• **new VideoTexture**(`scene`, `options`, `onReady`, `onEnd?`)

#### [#](#Parameters) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `scene` | [`Scene`](./Scene.html) | - |
| `options` | [`IVideoTextureOptions`](./../interfaces/IVideoTextureOptions.html) | - |
| `onReady` | (`vt`: [`VideoTexture`](./VideoTexture.html), `error?`: `Error`) => `void` | 创建成功时的回调。 |
| `onEnd?` | () => `void` | 播放结束时的回调。 |

## [#](#Properties-2) Properties

### [#](#onEnd) onEnd

• `Optional` **onEnd**: () => `void`

#### [#](#Type-declaration) Type declaration

▸ (): `void`

##### [#](#Returns) Returns

`void`

## [#](#Accessors-2) Accessors

### [#](#autoPause) autoPause

• `get` **autoPause**(): `boolean`

#### [#](#Returns-2) Returns

`boolean`

---

### [#](#height) height

• `get` **height**(): `number`

#### [#](#Returns-3) Returns

`number`

---

### [#](#state) state

• `get` **state**(): [`EVideoState`](./../enums/EVideoState.html)

当前视频纹理播放状态。

#### [#](#Returns-4) Returns

[`EVideoState`](./../enums/EVideoState.html)

---

### [#](#texture) texture

• `get` **texture**(): `default`

#### [#](#Returns-5) Returns

`default`

---

### [#](#width) width

• `get` **width**(): `number`

#### [#](#Returns-6) Returns

`number`

## [#](#Methods-2) Methods

### [#](#pause) pause

▸ **pause**(): `Promise`<`void`>

暂停当前播放的视频。
需要在基础库`v2.33.0`及以上支持。

#### [#](#Returns-7) Returns

`Promise`<`void`>

---

### [#](#play) play

▸ **play**(): `Promise`<`void`>

播放视频。

#### [#](#Returns-8) Returns

`Promise`<`void`>

---

### [#](#release) release

▸ **release**(): `void`

释放视频。

#### [#](#Returns-9) Returns

`void`

---

### [#](#resume) resume

▸ **resume**(): `Promise`<`void`>

唤醒已暂停的视频。
需要在基础库`v2.33.0`及以上支持。

#### [#](#Returns-10) Returns

`Promise`<`void`>

---

### [#](#seek) seek

▸ **seek**(`pos`): `Promise`<`any`>

从某处开始播放。

#### [#](#Parameters-2) Parameters

| Name | Type | Description |
| --- | --- | --- |
| `pos` | `number` | 事件，单位为s |

#### [#](#Returns-11) Returns

`Promise`<`any`>

---

### [#](#stop) stop

▸ **stop**(): `void`

停止播放视频。

#### [#](#Returns-12) Returns

`void`

Incorrect translation.