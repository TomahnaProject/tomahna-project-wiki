# `ParticleSystemBase`

- [`ThorResourceType`](./index.md#thorresourcetype-enum): `0x1D`
- Max. version: `0x2`

## `ParticleSystemBase` structure

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| header | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) |  |  |
| type | `uint32` |  | Must be 1 or 2, or Revelation will crash. |
| partsys | [`PSGenericSprite`](#psgenericsprite-structure) | `type == 1` |  |
| partsys | [`PSGenericGeometry`](#psgenericgeometry-structure) | `type == 2` |  |
| forces | [`Array`](../base.md#array-structure)<[`Force`](#force-structure)> |  |  |
| states | [`Array`](../base.md#array-structure)<[`SteadyState`](#steadystate-structure)> |  |  |

### `PSGenericSprite` structure

| Name | Type |
| :-- | :-- |
| base | [`PSGenericBase`](#psgenericbase-structure) |
| defaultSpriteWidth | `float32` |
| defaultSpriteHeight | `float32` |
| scaleParams | [`ScaleParams`](#scaleparams-struct) |
| isRotating | `bool` |
| rotation | [`VariableData`](#variabledata-structure)<`float32`> |
| isPendulumRotating | `bool` |
| pendulumRotationRange | [`VariableData`](#variabledata-structure)<`float32`> |
| pendulumRotationCycleTime | [`VariableData`](#variabledata-structure)<`float32`> |
| isTextureTiled | `bool` |
| usedTextureTiles | [`Array`](../base.md#array-structure)<`uint8`> |
| textureName | [`EncryptedString`](../base.md#encryptedstring-structure) |
| ??? | `uint32` |
| ??? | `uint32` |
| cylindricalBillboarding | `bool` |

### `PSGenericGeometry` structure

| Name | Type |
| :-- | :-- |
| base | [`PSGenericBase`](#psgenericbase-structure) |
| scale3DParams | [`Scale3DParams`](#scale3dparams-structure) |
| ??? | `bool` |

### `PSGenericBase` structure

| Name | Type |
| :-- | :-- |
| maxPartCount | `uint32` |
| emitterParams | [`EmitterParams`](#emitterparams-structure) |
| generationRate | `float32` |
| hasLifeTime | `bool` |
| ??? | [`VariableData`](#variabledata-structure)<`float32`>`[3]` |
| opacityParams | [`OpacityParams`](#opacityparams-structure) |
| isColorHSV | `bool` |
| colorParams | [`ColorParams`](#colorparams-structure) |
| bounceParams | [`BounceParams`](#bounceparams-structure) |
| deathPlaneParams | [`DeathPlaneParams`](#deathplaneparams-structure) |
| orbitalParams | [`OrbitalParams`](#orbitalparams-structure) |
| gravity | [`Vector3`](../base.md#vector3-structure) |

#### `EmitterParams` structure

| Name | Type |
| :-- | :-- |
| shapeType | [`ShapeType`](#shapetype-enum) |
| positionParams | `float32[3]` |
| velocityType | [`VelocityType`](#velocitytype-enum) |
| speed | [`VariableData`](#variabledata-structure)<`float32`> |
| velocityAngles | `float32[2]` |
| globalMatrixOffset | [`Vector3`](../base.md#vector3-structure) |
| globalMatrixRotation | [`Vector3`](../base.md#vector3-structure) |

###### `ShapeType` enum

| Name | Value |
| :-- | :-- |
| `Point` | `0x0` |
| `Rectangle` | `0x1` |
| `Circle` | `0x2` |
| `CircleEdge` | `0x3` |
| `Cylinder` | `0x4` |
| `CylinderEdge` | `0x5` |
| `Sphere` | `0x6` |
| `HalfSphere` | `0x7` |
| `Box` | `0x8` |

###### `VelocityType` enum

| Name | Value |
| :-- | :-- |
| ??? | `0x0` |
| ??? | `0x1` |
| ??? | `0x2` |

#### `OpacityParams` structure

Also called `LifeStageParameters<0>`.

| Name | Type |
| :-- | :-- |
| ??? | `bool` |
| ??? | `bool` |
| ??? | [`VariableData`](#variabledata-structure)<`float32`>`[3]` |

#### `ColorParams` structure

Also called `LifeStageParameters<1>`.

| Name | Type |
| :-- | :-- |
| ??? | `bool` |
| ??? | `bool` |
| ??? | [`VariableData`](#variabledata-structure)<[`Vector3`](../base.md#vector3-structure)>`[3]` |

#### `BounceParams` structure

| Name | Type |
| :-- | :-- |
| ??? | `bool` |
| plane | [`Plane`](../base.md#plane-structure) |
| speedLossFactor | `float32` |

#### `DeathPlaneParams` structure

| Name | Type |
| :-- | :-- |
| ??? | `bool` |
| killParticles | `bool` |
| planes | [`Array`](../base.md#array-structure)<[`Plane`](../base.md#plane-structure)> |

#### `OrbitalParams` structure

| Name | Type |
| :-- | :-- |
| ??? | `bool` |
| speed | [`VariableData`](#variabledata-structure)<`float32`> |
| radius | [`VariableData`](#variabledata-structure)<`float32`> |
| orient | `bool` |
| newGoalInterval | `float32` |
| newGoalAxisAdjust | `float32` |
| changeOrbitalForces | `bool` |
| changeOfOrbitalTime | [`VariableData`](#variabledata-structure)<`float32`> |
| nOrbitalForces | `uint32` |

#### `ScaleParams` struct

Also called `LifeStageParameters<2>`.

| Name | Type |
| :-- | :-- |
| ??? | `bool` |
| keepScaleRatio | `bool` |
| ??? | `bool` |
| ??? | [`VariableData`](#variabledata-structure)<[`Vector2`](../base.md#vector2-structure)>`[3]` |

#### `Scale3DParams` structure

Also called `LifeStageParameters<3>`.

| Name | Type |
| :-- | :-- |
| ??? | `bool` |
| keepScaleRatio | `bool` |
| ??? | `bool` |
| ??? | [`VariableData`](#variabledata-structure)<[`Vector3`](../base.md#vector3-structure)>`[3]` |

#### `VariableData`<`Type`> structure {#variabledata-structure}

A `VariableData` describes the bounds within which a variable is to be randomised.

| Name | Type |
| :-- | :-- |
| min | `Type` |
| max | `Type` |

### `Force` structure

| Name | Type | Conditoin | Description |
| :-- | :-- | :-- | --- |
| type | `uint32` |  | Must be 1, 2, 3, or 4, or Revelation will crash. |
| data | [`FWind`](#fwind-structure) | `type == 1` |  |
| data | [`FOrbital`](#forbital-structure) | `type == 2` |  |
| data | [`FFriction`](#ffriction-structure) | `type == 3` |  |
| data | [`FRayRepulsor`](#frayrepulsor-structure) | `type == 4` |  |

#### `FWind` structure

| Name | Type |
| :-- | :-- |
| name | [`EncryptedString`](../base.md#encryptedstring-structure) |
| localMatrixOffset | [`Vector3`](../base.md#vector3-structure) |
| localMatrixRotation | [`Vector3`](../base.md#vector3-structure) |
| maxForces | `float32` |
| ??? | `float32` |

#### `FOrbital` structure

| Name | Type |
| :-- | :-- |
| name | [`EncryptedString`](../base.md#encryptedstring-structure) |
| localMatrixOffset | [`Vector3`](../base.md#vector3-structure) |
| localMatrixRotation | [`Vector3`](../base.md#vector3-structure) |
| id | `uint32` |
| ??? | `float32` |
| radialTargetSpeedAdjust | `float32` |
| ??? | `float32` |

#### `FFriction` structure

| Name | Type |
| :-- | :-- |
| name | [`EncryptedString`](../base.md#encryptedstring-structure) |
| friction | `float32` |

#### `FRayRepulsor` structure

| Name | Type |
| :-- | :-- |
| name | [`EncryptedString`](../base.md#encryptedstring-structure) |
| localMatrixOffset | [`Vector3`](../base.md#vector3-structure) |
| localMatrixRotation | [`Vector3`](../base.md#vector3-structure) |
| ??? | `float32` |
| ??? | `float32` |
| maxDistance | `float32` |

### `SteadyState` structure

| Name | Type |
| :-- | :-- |
| id | `uint32` |
| ??? | [`Array`](../base.md#array-structure)<`uint8`> |
