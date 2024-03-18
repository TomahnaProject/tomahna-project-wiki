# `Video`

A `Video` describes the properties and location of a Bink (`.bik`) video file.

[`ThorResourceType`](./index.md#thorresourcetype-enum): `0x29`

Max. version: `0x5`

## `Video` structure

| Name | Type | Condition | Description |
| :-- | --: | :-- | --- |
| hdr | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) |  | Header. |
| ??? | `bool` |  | Revelation's code appears to ignore this field. |
| path | [`EncryptedString`](../base.md#encryptedstring-structure) |  | Virtual path to video file. |
| hasAlpha | `bool` |  | Whether the video contains transparency data. |
| preload | `bool` |  | Whether the video should be preloaded. |
| isMonochrome | `bool` |  | Whether the video is monochrome. |
| dataRate | `uint32` |  |  |
| hasKeyframes | `bool` |  | Whether this resource contains keyframes for easy seeking. |
| keyframes | [`ThorResource`](./index.md#thorresource-structure) | `hasKeyframes` | [`ContainerResource`](./containerresource.md) called `"keyframe"` containing [`VariableResource`](./variableresource.md)s with `uint32` type. Resource is ignored if not a `ContainerResource`, and contained resources are ignored if not `VariableResource`. However, `VariableResource`s **must** have `uint32` type, or Revelation will crash. |
