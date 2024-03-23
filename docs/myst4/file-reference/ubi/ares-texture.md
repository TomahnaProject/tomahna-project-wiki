# `ares::Texture`

An `ares::Texture` contains a texture and some relevant parsing information.

It is unknown what the distinction is between `ares::Texture` and `ares::TextureFrame`; they share the same serialization routine.

[`UbiResourceType`](./index.md#ubiresourcetype-string): `"ares::Texture"` and `"ares::TextureFrame"`

## `ares::Texture` structure

| Name | Type | Condition | Description |
| :-- | --: | :-- | --- |
| name | [`BasicString`](../base.md#basicstring-structure) | `ver >= 0x5` | Instance name. |
| formatLen | `uint8` |  | Length of format string. |
| format | `uint8`[`formatLen`] |  | Format string. |
| accessPerms | `uint32` |  |  |
| transparencyType | `uint32` |  |  |
| formatHint | `uint32` | `ver >= 0xA` |  |
| nFiles | `uint8` |  |  |
| textureFile | [`Array`](../base.md#array-structure)<`uint8`> |  | Texture file. |
