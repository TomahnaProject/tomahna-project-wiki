# `TextureBox`

- [`ThorResourceType`](./index.md#thorresourcetype-enum): `0xF`
- Max. version: `0x5`

A `TextureBox` describes a single-layer texture box.

## `TextureBox` structure

| Name | Type | Description |
| :-- | :-- | --- |
| header | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) |  |
| bftexPath | [`EncryptedString`](../base.md#encryptedstring-structure) | Virtual path to the [`BigFile`](../bigfile.md#bigfile-structure) containing the texture sets. During loading, this BigFile is mounted to `/bftex`. |
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

| Name | Type |
| :-- | :-- |
| ??? | `uint32` |
| ??? | [`Array`](../base.md#array-structure)<[`EncryptedString`](../base.md#encryptedstring-structure)> |
