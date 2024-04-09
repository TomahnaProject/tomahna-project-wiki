# `TextureResource`

- [`ThorResourceType`](./index.md#thorresourcetype-enum): `0x27`
- Max. version: `0x2`

A `TextureResource` contains a single texture image, or a reference to one if it is localised.

## `TextureResource` structure

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| header | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) |  |  |
| isLocalised | `bool` |  | Indicates whether this texture has localised content. |
| path | [`BasicString`](../base.md#basicstring-structure) | `isLocalised` | Virtual path to localised texture file. Never observed to refer to anything but raw PNG files. |
| format | [`EncryptedString`](../base.md#encryptedstring-structure) | `!isLocalised` | Format of `data`. Never observed to be anything other than "png". |
| data | [`Array`](../base.md#array-structure)<`uint8`> | `!isLocalised` |  |
