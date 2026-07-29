[xr-frame](./../) / [Exports](./../modules.html) / IDownloader

# [#](#Interface-IDownloader) Interface: IDownloader

下载器。

## [#](#Table-of-contents) Table of contents

### [#](#Properties) Properties

- [REAL\_DOWNLOADER](./IDownloader.html#REAL_DOWNLOADER)
- [inWX](./IDownloader.html#inWX)

### [#](#Methods) Methods

- [LOAD](./IDownloader.html#LOAD)

## [#](#Properties-2) Properties

### [#](#REAL-DOWNLOADER) REAL\_DOWNLOADER

• **REAL\_DOWNLOADER**: [`IRealDownloader`](./IRealDownloader.html)

---

### [#](#inWX) inWX

• **inWX**: `boolean`

## [#](#Methods-2) Methods

### [#](#LOAD) LOAD

▸ **LOAD**(`options`): `void`

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