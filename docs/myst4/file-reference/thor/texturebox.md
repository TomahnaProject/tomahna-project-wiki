# `TextureBox`

A `TextureBox` describes a single-layer texture box.

[`ThorResourceType`](./index.md#thorresourcetype-enum): `0xF`

Max. version: `0x5`

## `TextureBox` structure

| Name | Type | Description |
| :-- | --: | --- |
| hdr | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) | Header. |
| ??? | [`EncryptedString`](../base.md#encryptedstring-structure) |  |
| radius | `float32` |  |
| isZBox | `bool` |  |
| zNear | `float32` |  |
| zFar | `float32` |  |
| zExponent | `float32` |  |
| isLayerMask | `bool` |  |
| layerIndex | `uint32` |  |
| components | [`Array`](../base.md#array-structure)<[`EncryptedString`](../base.md#encryptedstring-structure)> |  |
| states | [`Array`](../base.md#array-structure)<[`StateDesc`](#statedesc-structure)> |  |

### `StateDesc` structure

| Name | Type | Description |
| :-- | --: | --- |
| ??? | `uint32` |  |
| ??? | [`Array`](../base.md#array-structure)<[`EncryptedString`](../base.md#encryptedstring-structure)> |  |
