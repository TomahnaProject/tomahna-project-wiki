# `RailResource`

A `RailResource` describes a rail along which a hotspot can be dragged.

[`ThorResourceType`](./index.md#thorresourcetype-enum): `0x1F`

Max. version: `0x1`

## `RailResource` structure

| Name | Type | Description |
| :-- | --: | --- |
| hdr | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) | Header. |
| hotspotResName | [`EncryptedString`](../base.md#encryptedstring-structure) | Name of the [`GeometryResource`](./geometryresource.md) which describes the draggable hotspot for this rail. |
| initialVertex | `uint16` |  |
| directionType | [`DirectionType`](#directiontype-enum) |  |
| sensitivity | `float32` |  |
| snapFactor | `float32` |  |
| maxAngle | `float32` |  |
| ??? | `bool` |  |
| orientationX | `float32` |  |
| orientationY | `float32` |  |
| vertices | [`Array`](../base.md#arrayt-structure)<[`RailVertex`](#railvertex-structure)> |  |

### `DirectionType` enum

| Name | Value |
| :-- | --: |
| `Forward` | `0x0` |
| `Backward` | `0x1` |
| `Bidirectional` | `0x2` |

### `RailVertex` structure

| Name | Type | Description |
| :-- | --: | --- |
| ??? | [`Vector3`](../base.md#vector3-structure) |  |
| referenceIn3D | [`Vector3`](../base.md#vector3-structure) |  |
| referenceOut3D | [`Vector3`](../base.md#vector3-structure) |  |
