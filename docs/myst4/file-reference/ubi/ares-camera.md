# `ares::Camera`

`ares::Camera` is a base for [`ares::CameraOrthogonal`](#arescameraorthogonal) and [`ares::CameraPerspective`](#arescameraperspective).

## `ares::Camera` structure

| Name | Type | Condition |
| :-- | :-- | :-- |
| name | [`BasicString`](../base.md#basicstring-structure) | `version >= 0x5` |
| matrix | [`Matrix44`](../base.md#matrix44-structure) |  |
| frustumLeft | `float32` |  |
| frustumRight | `float32` |  |
| frustumBottom | `float32` |  |
| frustumTop | `float32` |  |
| frustumNear | `float32` |  |
| frustumFar | `float32` |  |
| viewportPosX | `float32` |  |
| viewportPosY | `float32` |  |
| viewportWidth | `float32` |  |
| viewportHeight | `float32` |  |
| sortModeOpaque | `uint32` |  |
| sortModeTransparent | `uint32` |  |

## `ares::CameraOrthogonal`

- [`UbiResourceType`](./index.md#ubiresourcetype-string): `"ares::CameraOrthogonal"`

### `ares::CameraOrthogonal` structure

| Name | Type |
| :-- | :-- |
| base | [`ares::Camera`](#arescamera-structure) |
| pixelAspectRatio | `float32` |
| fieldOfView | `float32` |

## `ares::CameraPerspective`

- [`UbiResourceType`](./index.md#ubiresourcetype-string): `"ares::CameraOrthogonal"`

### `ares::CameraPerspective` structure

| base | Type | Description |
| :-- | :-- | --- |
| base | [`ares::Camera`](#arescamera-structure) |  |
| pixelAspectRatio | `float32` |  |
| fieldOfViewHorizontal | `float32` |  |
| isFieldOfViewHorizontal | `bool` | If `false`, field of view is set to 0.0. |
