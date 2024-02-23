# `Subtitle`

A `Subtitle` contains localised subtitles to accompany speech samples.

[`ThorResourceType`](./index.md#thorresourcetype-enum): `0x24`

## `Subtitle` structure

| Name | Type | Description |
| :-- | --: | --- |
| hdr | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) | Header. |
| ??? | `int32` | Revelation's code appears to ignore this field. Never observed to be anything other than `0x1`. |
| soundName | [`BasicString`](../base.md#basicstring-structure) | Full name of the sound resource to sync to. |
| captions | [`Array`](../base.md#arrayt-structure)<[`Caption`](#caption-structure)> | Captions. In the source material, all captions will have a start time equal to the end time of the caption before it. It is unconfirmed whether this is required. |

### `Caption` structure

| Name | Type | Description |
| :-- | --: | --- |
| start | `float32` | Start time. |
| end | `float32` | End time. |
| text | [`BasicWString`](../base.md#basicwstring-structure) | Text. Can be empty. |
