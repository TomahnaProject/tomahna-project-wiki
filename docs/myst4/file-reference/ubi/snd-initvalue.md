# `snd::InitValue`

A `snd::InitValue` is a getter interface for some initialisation value. The following types exist:

| Type | [`UbiResourceType`](./index.md#ubiresourcetype-string) | Descrpition |
| :-- | :-- | :-- |
| [`snd::InitValueConst`](#sndinitvalueconsttype-structure)<`uint32`> | `"snd::InitValueConst < ubiU32 >"` |  |
| [`snd::InitValueConst`](#sndinitvalueconsttype-structure)<`int32`> | `"snd::InitValueConst < ubiS32 >"` |  |
| [`snd::InitValueConst`](#sndinitvalueconsttype-structure)<`float32`> | `"snd::InitValueConst < ubiF32 >"` |  |
| [`snd::InitValueConst`](#sndinitvalueconsttype-structure)<[`Vector3`](../base.md#vector3-structure)> | `"snd::InitValueConst < ubi::Vector3 >"` |  |
| [`snd::InitValueRange`](#sndinitvaluerangetype-structure)<`uint32`> | `"snd::InitValueRange < ubiU32 >"` |  |
| [`snd::InitValueRange`](#sndinitvaluerangetype-structure)<`int32`> | `"snd::InitValueRange < ubiS32 >"` |  |
| [`snd::InitValueRange`](#sndinitvaluerangetype-structure)<`float32`> | `"snd::InitValueRange < ubiF32 >"` |  |
| [`snd::InitValueRange`](#sndinitvaluerangetype-structure)<[`Vector3`](../base.md#vector3-structure)> | `"snd::InitValueRange < ubi::Vector3 >"` | Though a vec3 is kept in memory, the class only works with the `x` element. |
| [`snd::InitValueSequence`](#sndinitvaluesequencetype-structure)<`uint32`> | `"snd::InitValueSequence < ubiU32 >"` |  |
| [`snd::InitValueSequence`](#sndinitvaluesequencetype-structure)<`int32`> | `"snd::InitValueSequence < ubiS32 >"` |  |
| [`snd::InitValueSequence`](#sndinitvaluesequencetype-structure)<`float32`> | `"snd::InitValueSequence < ubiF32 >"` |  |
| [`snd::InitValueSequence`](#sndinitvaluesequencetype-structure)<[`Vector3`](../base.md#vector3-structure)> | `"snd::InitValueSequence < ubi::Vector3 >"` |  |

## `snd::InitValueConst`<`Type`> structure

Getter that returns the same, constant value.

| Name | Type |
| :-- | :-- |
| value | `Type` |

## `snd::InitValueRange`<`Type`> structure

Getter that returns a random value within a range.

| Name | Type |
| :-- | :-- |
| min | `Type` |
| max | `Type` |

## `snd::InitValueSequence`<`Type`> structure

Getter that returns a value from a looping sequence of `InitValue`s.

| Name | Type | Description |
| :-- | :-- | :-- |
| seq | [`Array`](../base.md#array-structure)<[`UbiSubResource`](./index.md#ubisubresource-structure)> | Revelation assumes all `type` to be one of the `"snd::InitValue"` types with the same `Type`. |
| iterType | `uint32` | Enum which involves the iteration method for `seq`. Never observed to be anything other than `0x2`. Only known effect is for value `0x0`: every loop through the sequence, the order is randomised. If the value is not `0x0`, every loop through the sequence is ordered from begin to end. |
