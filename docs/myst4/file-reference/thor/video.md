# `Video`

- [`ThorResourceType`](./index.md#thorresourcetype-enum): `0x29`
- Max. version: `0x5`

A `Video` describes the properties and location of a Bink (`.bik`) video file.

## `Video` structure

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| header | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) |  |  |
| ??? | `bool` |  | Revelation's code appears to ignore this field. |
| path | [`EncryptedString`](../base.md#encryptedstring-structure) |  | Virtual path to video file. |
| hasAlpha | `bool` |  | Indicates whether the video contains transparency data. |
| preload | `bool` |  | Indicates whether the video should be preloaded. |
| isMonochrome | `bool` |  |  |
| dataRate | `uint32` |  |  |
| hasKeyframes | `bool` |  |  |
| keyframes | [`ThorResource`](./index.md#thorresource-structure) | `hasKeyframes` | Used for easy seeking through the video. Resource is ignored if not a [`ContainerResource`](./containerresource.md), and contained resources are ignored if not `VariableResource`. However, the `VariableResource`s must have `uint32` type, or Revelation will crash. |
