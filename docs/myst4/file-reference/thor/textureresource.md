# `TextureResource`

A `TextureResource` contains a single texture image, or a reference to one if it is localised.

[`ThorResourceType`](./index.md#thorresourcetype-enum): `0x27`

Max. version: `0x2`

## `TextureResource` structure

| Name | Type | Condition | Description |
| :-- | --: | :-- | --- |
| hdr | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) |  | Header. |
| isLocalised | `bool` |  | Indicator of whether this texture has different localised versions. |
| path | [`BasicString`](../base.md#basicstring-structure) | `isLocalised` | Virtual path to localised texture file. Never observed to refer to anything but raw PNG files. |
| data | [`ImageData`](#imagedata-structure) | `!isLocalised` | Image data. |

### `ImageData` structure

| Name | Type | Description |
| :-- | --: | --- |
| format | [`EncryptedString`](../base.md#encryptedstring-structure) | Format of `data`. Never observed to be anything other than "png". |
| data | [`Array`](../base.md#array-structure)<`uint8`> | Data. |
