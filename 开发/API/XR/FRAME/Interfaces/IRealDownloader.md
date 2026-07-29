[xr-frame](./../) / [Exports](./../modules.html) / IRealDownloader

# [#](#Interface-IRealDownloader) Interface: IRealDownloader

外部需要注入的下载器接口。

## [#](#Table-of-contents) Table of contents

### [#](#Methods) Methods

- [load](./IRealDownloader.html#load)

## [#](#Methods-2) Methods

### [#](#load) load

▸ **load**(`options`): `void`

#### [#](#Parameters) Parameters

| Name | Type |
| --- | --- |
| `options` | `Object` |
| `options.onError` | (`error`: `Error`) => `void` |
| `options.onLoad` | (`res`: { `data`: `ArrayBuffer` ; `filePath`: `string` }) => `void` |
| `options.encoding` | `"binary"` | `"utf-8"` |
| `options.src` | `string` |

#### [#](#Returns) Returns

`void`

Incorrect translation.