# `RailResource`

- [`ThorResourceType`](./index.md#thorresourcetype-enum): `0x1F`
- Max. version: `0x1`

A `RailResource` describes a rail along which a hotspot can be dragged.

## `RailResource` structure

| Name | Type | Description |
| :-- | :-- | --- |
| header | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) |  |
| hotspotName | [`EncryptedString`](../base.md#encryptedstring-structure) | Name of the [`GeometryResource`](./geometryresource.md) which describes the draggable hotspot for this rail. |
| initialVertex | `uint16` |  |
| directionType | [`DirectionType`](#directiontype-enum) |  |
| sensitivity | `float32` |  |
| snapFactor | `float32` |  |
| maxAngle | `float32` |  |
| isCyclic | `bool` | Indicates whether the first and last rail segments connect back to each other, i.e. whether the rail's hotspot can be dragged past the last rail segment to the first (and/or vice versa). |
| orientationX | `float32` |  |
| orientationZ | `float32` |  |
| vertices | [`Array`](../base.md#array-structure)<[`RailVertex`](#railvertex-structure)> | If `!isCyclic`, `vertices[0].in` and `vertices[vertices.len-1].out` are ignored. |

### `DirectionType` enum

`DirectionType` describes the direction in which a hotspot can be dragged along a rail.

| Name | Value |
| :-- | :-- |
| `Forward` | `0x0` |
| `Backward` | `0x1` |
| `Bidirectional` | `0x2` |

### `RailVertex` structure

A `RailVertex` describes a vertex along a cubic Bézier curve.

| Name | Type | Description |
| :-- | :-- | --- |
| pos | [`Vector3`](../base.md#vector3-structure) | Position. |
| in | [`Vector3`](../base.md#vector3-structure) |  |
| out | [`Vector3`](../base.md#vector3-structure) |  |
