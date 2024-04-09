# `Subtitle`

- [`ThorResourceType`](./index.md#thorresourcetype-enum): `0x24`
- Max. version: `0x1`

A `Subtitle` contains localised subtitles to accompany speech samples.

## `Subtitle` structure

| Name | Type | Description |
| :-- | :-- | --- |
| header | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) |  |
| ??? | `int32` | Revelation's code appears to ignore this field. Never observed to be anything other than `0x1`. |
| soundName | [`BasicString`](../base.md#basicstring-structure) | Full name of the sound resource to sync to. |
| captions | [`Array`](../base.md#array-structure)<[`Caption`](#caption-structure)> | In source material, all captions have a start time equal to the end time of the caption before it. It is unconfirmed whether this is required. |

### `Caption` structure

| Name | Type | Description |
| :-- | :-- | --- |
| startTime | `float32` |  |
| endTime | `float32` |  |
| text | [`BasicWString`](../base.md#basicwstring-structure) | Can be empty. |
