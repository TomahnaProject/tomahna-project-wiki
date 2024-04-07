# `MOREActor::ActorModel`

- [`UbiResourceType`](./index.md#ubiresourcetype-string): `"MOREActor::ActorModel"`

TODO

## `MOREActor::ActorModel` structure

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| bonesName | [`BasicString`](../base.md#basicstring-structure) | `ver < 0x6` | Revelation's code appears to ignore this field. |
| bonesGeometricFileName | [`BasicString`](../base.md#basicstring-structure) | `ver < 0x6` | Revelation's code appears to ignore this field. |
| bones | [`Array`](../base.md#array-structure)<[`BoneInfo`](#boneinfo-structure)> | `ver >= 0x6 && ver < 0x8` |  |
| bones | [`Array`](../base.md#array-structure)<[`BoneModel`](#bonemodel-structure)> | `ver >= 0x8` |  |
| eventEmitters | [`Array`](../base.md#array-structure)<[`EventEmitterInfo`](#eventemitterinfo-structure)> | `ver >= 0x3 && ver < 0x8` |  |
| eventEmitters | [`Array`](../base.md#array-structure)<[`EventEmitterModel`](#eventemittermodel-structure)> | `ver >= 0x8` |  |
| soundEmitters | [`Array`](../base.md#array-structure)<[`SoundEmitterInfo`](#soundemitterinfo-structure)> | `ver < 0x8` |  |
| soundEmitters | [`Array`](../base.md#array-structure)<[`BaseEmitterModel`](#baseemittermodel-structure)> | `ver >= 0x8` |  |
| stateModels | [`Array`](../base.md#array-structure)<[`BaseTrackContainerModel`](#basetrackcontainermodel-structure)> | `ver => 0xA` |  |
| channels | [`Array`](../base.md#array-structure)<[`ChannelInfo`](#channelinfo-structure)> | `ver < 0x8` |  |
| channels | [`Array`](../base.md#array-structure)<[`ChannelModel`](#channelmodel-structure)> | `ver >= 0x8` |  |
| graphicObjectNames | [`Array`](../base.md#array-structure)<[`BasicString`](../base.md#basicstring-structure)> | `ver >= 0x6` |  |

### `BaseHierarchyModel` structure

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| name | [`BasicString`](../base.md#basicstring-structure) |  |  |
| fatherIndex | `int16` |  |  |
| type | `uint32` |  |  |
| position | ??? |  | Type changes based on `type` (`0x0`, `0x1` or `0x2`). |

!!! note
    If `type` is not any of the values listed above, Revelation will crash.

### `BaseRotationModel` structure

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| type | `uint32` |  |  |
| rotation | ??? |  | Type changes based on `type` (`0x0`, `0x1`, `0x2`, `0x3` or `0x4`). |

!!! note
    If `type` is not any of the values listed above, Revelation will crash.

### `BaseEmitterModel` structure

| Name | Type | Description |
| :-- | :-- | --- |
| bhm | [`BaseHierarchyModel`](#basehierarchymodel-structure) |  |
| box | [`Box`](../base.md#box-structure) |  |
| trackNames | [`Array`](../base.md#array-structure)<[`BasicString`](../base.md#basicstring-structure)> |  |

### `BaseTrackContainerModel` structure

| Name | Type | Description |
| :-- | :-- | --- |
| name | [`BasicString`](../base.md#basicstring-structure) |  |
| trackNames | [`Array`](../base.md#array-structure)<[`BasicString`](../base.md#basicstring-structure)> |  |

### `BoneInfo` structure

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| name | [`BasicString`](../base.md#basicstring-structure) |  |  |
| positionName | [`BasicString`](../base.md#basicstring-structure) |  |  |
| rotationName | [`BasicString`](../base.md#basicstring-structure) |  |  |
| scaleValueName | [`BasicString`](../base.md#basicstring-structure) | `ver >= 0x7` |  |
| scaleOrientationName | [`BasicString`](../base.md#basicstring-structure) | `ver >= 0x7` |  |
| useScale | `bool` | `ver >= 0x7` |  |
| fatherIndex | `int16` |  |  |
| defaultPosition | [`Vector3`](../base.md#vector3-structure) |  |  |
| defaultRotation | [`Quaternion`](../base.md#vector4-quaternion-structure) |  |  |
| scaleValue | [`Vector3`](../base.md#vector3-structure) | `ver < 0x7` |  |
| scaleOrientation | [`Quaternion`](../base.md#vector4-quaternion-structure) | `ver < 0x7` |  |
| matrixDeterminant | `float32` | `ver < 0x7` | `scaleValue *= matrixDeterminant` |
| defaultScaleValue | [`Vector3`](../base.md#vector3-structure) | `ver >= 0x7` |  |
| defaultScaleOrientation | [`Quaternion`](../base.md#vector4-quaternion-structure) | `ver >= 0x7` |  |

### `BoneModel` structure

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| bhm | [`BaseHierarchyModel`](#basehierarchymodel-structure) |  |  |
| brm | [`BaseRotationModel`](#baserotationmodel-structure) |  |  |
| type | `uint32` |  |  |
| scale | [`AnimScale`](#animscale-structure) | `type == 0x0` |  |
| scale | [`ConstScale`](#constscale-structure) | `type == 0x1` |  |

!!! note
    If `type` is not any of the values listed above, Revelation will crash.

#### `AnimScale` structure

| Name | Type | Description |
| :-- | :-- | --- |
| const | [`ConstAnim`](#constscale-structure) |  |
| valueName | [`BasicString`](../base.md#basicstring-structure) |  |
| rotationName | [`BasicString`](../base.md#basicstring-structure) |  |

#### `ConstScale` structure

| Name | Type | Description |
| :-- | :-- | --- |
| value | [`Vector3`](../base.md#vector3-structure) |  |
| rotation | [`Quaternion`](../base.md#vector4-quaternion-structure) |  |

### `EventEmitterInfo` structure

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| name | [`BasicString`](../base.md#basicstring-structure) |  |  |
| positionName | [`BasicString`](../base.md#basicstring-structure) |  |  |
| rotationName | [`BasicString`](../base.md#basicstring-structure) |  |  |
| fatherIndex | `int16` |  |  |
| defaultPosition | [`Vector3`](../base.md#vector3-structure) |  |  |
| defaultRotation | [`Quaternion`](../base.md#vector4-quaternion-structure) |  |  |
| box | [`Box`](../base.md#box-structure) | `ver >= 0x4` |  |
| eventTrackNames | [`Array`](../base.md#array-structure)<[`BasicString`](../base.md#basicstring-structure)> |  |  |

### `EventEmitterModel` structure

| Name | Type | Description |
| :-- | :-- | --- |
| bem | [`BaseEmitterModel`](#baseemittermodel-structure) |  |
| brm | [`BaseRotationModel`](#baserotationmodel-structure) |  |

### `SoundEmitterInfo` structure

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| name | [`BasicString`](../base.md#basicstring-structure) |  |  |
| positionName | [`BasicString`](../base.md#basicstring-structure) |  |  |
| fatherIndex | `int16` |  |  |
| defaultPosition | [`Vector3`](../base.md#vector3-structure) |  |  |
| box | [`Box`](../base.md#box-structure) | `ver >= 0x4` |  |
| soundTrackNames | [`Array`](../base.md#array-structure)<[`BasicString`](../base.md#basicstring-structure)> |  |  |

### `ChannelInfo` structure

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| name | [`BasicString`](../base.md#basicstring-structure) |  | If `ver < 0x6`, serialization code describes this as `geometricObjectName` instead, but still puts it in the same struct field. |
| graphicObjectIDs | [`Array`](../base.md#array-structure)<`uint16`> | `ver >= 0x6` |  |
| boneIDs | [`Array`](../base.md#array-structure)<`uint16`> |  |  |
| isDeformable | `bool` | `ver >= 0x5` | If `ver < 0x5`, this field is `boneIDs.len > 1`. |

### `ChannelModel` structure

| Name | Type | Description |
| :-- | :-- | --- |
| name | [`BasicString`](../base.md#basicstring-structure) |  |
| isDeformable | `bool` |  |
| isMultipleMeshes | `bool` |  |
| isVisibilityAnimated | `bool` |  |
| boneIDs | [`Array`](../base.md#array-structure)<`uint16`> |  |
| graphicObjectIDs | [`Array`](../base.md#array-structure)<`uint16`> |  |
