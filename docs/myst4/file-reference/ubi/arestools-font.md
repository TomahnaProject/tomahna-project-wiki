# `ares_tools::Font`

- [`UbiResourceType`](./index.md#ubiresourcetype-string): `"ares_tools::Font"`

An `ares_tools::Font` describes a font. They are contained exclusively in `.fnt` files found in `data.m4b/common/common.m4b/font`.

## `ares_tools::Font` structure

| Name | Type | Description |
| :-- | :-- | --- |
| name | [`BasicString`](../base.md#basicstring-structure) | Instance name. |
| nTextures | `uint32` | Number of `.tga` texture files containing the font's letters. They are in the same directory as the `.fnt` file with a one-indexed `_%d` suffix in the filename. |
| letters | [`Array`](../base.md#array-structure)<[`Letter`](#letter-structure)> | Letters. |

### `Letter` structure

| Name | Type | Description |
| :-- | :-- | --- |
| code | `uint16` | Code point. |
| lowerLeftTexCoord | [`Vector2`](../base.md#vector2-structure) |  |
| upperRightTexCoord | [`Vector2`](../base.md#vector2-structure) |  |
| textureIndex | `int` | Index of texture file containing this letter. |

The floats in both tex coords consider the bottom-left (0.0, 0.0), and the upper right (1.0, 1.0).
