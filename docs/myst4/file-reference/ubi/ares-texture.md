# `ares::Texture`

- [`UbiResourceType`](./index.md#ubiresourcetype-string): `"ares::Texture"` and `"ares::TextureFrame"`

An `ares::Texture` contains a texture and some relevant parsing information.

It is unknown what the distinction is between `ares::Texture` and `ares::TextureFrame`; they share the same serialisation routine.

## `ares::Texture` structure

| Name | Type | Condition |
| :-- | :-- | :-- |
| name | [`BasicString`](../base.md#basicstring-structure) | `version >= 0x5` |
| formatLen | `uint8` |  |
| format | `uint8`[`formatLen`] |  |
| accessPerms | `uint32` |  |
| transparencyType | `uint32` |  |
| formatHint | `uint32` | `version >= 0xA` |
| nFiles | `uint8` |  |
| textureFile | [`Array`](../base.md#array-structure)<`uint8`> |  |
