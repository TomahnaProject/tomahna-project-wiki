# `ares::Camera`

`ares::Camera` is a base for [`ares::CameraOrthogonal`](#arescameraorthogonal) and [`ares::CameraPerspective`](#arescameraperspective).

## `ares::Camera` structure

| Name | Type | Condition | Description |
| :-- | --: | :-- | --- |
| name | [`BasicString`](../base.md#basicstring-structure) | `ver >= 0x5` | Instance name. |
| matrix | [`Matrix44`](../base.md#matrix44-structure) |  |  |
| frustumLeft | `float32` |  |  |
| frustumRight | `float32` |  |  |
| frustumBottom | `float32` |  |  |
| frustumTop | `float32` |  |  |
| frustumNear | `float32` |  |  |
| frustumFar | `float32` |  |  |
| viewportPosX | `float32` |  |  |
| viewportPosY | `float32` |  |  |
| viewportWidth | `float32` |  |  |
| viewportHeight | `float32` |  |  |
| sortModeOpaque | `uint32` |  |  |
| sortModeTransparent | `uint32` |  |  |

## `ares::CameraOrthogonal`

- [`UbiResourceType`](./index.md#ubiresourcetype-string): `"ares::CameraOrthogonal"`

TODO

### `ares::CameraOrthogonal` structure

| Name | Type | Description |
| :-- | --: | --- |
| camera | [`ares::Camera`](#arescamera-structure) | Base camera. |
| pixelAspectRatio | `float32` |  |
| fov | `float32` | Field of view. |

## `ares::CameraPerspective`

- [`UbiResourceType`](./index.md#ubiresourcetype-string): `"ares::CameraOrthogonal"`

TODO

### `ares::CameraPerspective` structure

| Name | Type | Description |
| :-- | --: | --- |
| camera | [`ares::Camera`](#arescamera-structure) | Base camera. |
| pixelAspectRatio | `float32` |  |
| fovHorizontal | `float32` | Horizontal field of view. |
| isFOVHorizontal | `bool` | If false, FOV is set to 0.0. |
