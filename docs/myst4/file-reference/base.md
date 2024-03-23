# Base types

## `FileMagic` string

With some exceptions, all asset files have a `FileMagic` at the start of the file. It can be one of `"ubi/b0-l"` and `"ubi/b0-b"`, which indicate whether the file is little- or big-endian respectively. However, only `"ubi/b0-l"`, the little-endian variant, has ever been observed in the wild.

## `BasicString` structure

The basic UTF-16 string used all over the place. Sometimes referred to as `ubistring`.

| Name | Type | Description |
| :-- | --: | --- |
| len | `uint32` | Length of the string. |
| s | `char`\[`len`\] | The string. |

## `BasicWString` structure

Same as [`BasicString`](#basicstring-structure), except with UTF-16 encoding.

| Name | Type | Description |
| :-- | --: | --- |
| len | `uint32` | Length of the string. |
| s | `wchar_t`\[`len`\] | The string. |

## `EncryptedString` structure

Same as [`BasicString`](#basicstring-structure), except all `char`s are "swizzled". That is to say, for every byte `b` of `s`, apply `(b & 0xAA) >> 1 | (b & 0x55) << 1` to (un)swizzle.

| Name | Type | Description |
| :-- | --: | --- |
| len | `uint32` | Length of the string. |
| s | `char`\[`len`\] | The string. |

## `Vector2` structure

Sometimes referred to as `vec2`.

| Name | Type | Description |
| :-- | --: | --- |
| x | `float32` |  |
| y | `float32` |  |

## `Vector3` structure

Sometimes referred to as `vec3`.

| Name | Type | Description |
| :-- | --: | --- |
| x | `float32` |  |
| y | `float32` |  |
| z | `float32` |  |

## `Vector4` / `Quaternion` structure

Sometimes referred to as `vec4` or `quat` respectively.

| Name | Type | Description |
| :-- | --: | --- |
| x | `float32` |  |
| y | `float32` |  |
| z | `float32` |  |
| w | `float32` |  |

## `Matrix22` structure

| Name | Type | Description |
| :-- | --: | --- |
| x | [`Vector2`](#vector2-structure) |  |
| y | [`Vector2`](#vector2-structure) |  |

## `Matrix33` structure

| Name | Type | Description |
| :-- | --: | --- |
| x | [`Vector3`](#vector3-structure) |  |
| y | [`Vector3`](#vector3-structure) |  |
| z | [`Vector3`](#vector3-structure) |  |

## `Matrix44` structure

| Name | Type | Description |
| :-- | --: | --- |
| x | [`Vector4`](#vector4-quaternion-structure) |  |
| y | [`Vector4`](#vector4-quaternion-structure) |  |
| z | [`Vector4`](#vector4-quaternion-structure) |  |
| w | [`Vector4`](#vector4-quaternion-structure) |  |

## `Color` structure

| Name | Type | Description |
| :-- | --: | --- |
| r | `float32` | Red. |
| g | `float32` | Green. |
| b | `float32` | Blue. |
| a | `float32` | Alpha. |

## `Array`<`T`> structure {#array-structure}

| Name | Type | Description |
| :-- | --: | --- |
| len | `uint32` | Length of the array. |
| elements | `T`\[`len`\] | Elements of the array. |

## `PairArray`<`K`, `V`> structure {#pairarray-structure}

| Name | Type | Description |
| :-- | --: | --- |
| len | `uint32` | Length of the array. |
| elements | [`Pair`](#pair-structure)<`K`, `V`>\[`len`\] | Elements of the array. |

### `Pair`<`K`, `V`> structure {#pair-structure}

| Name | Type | Description |
| :-- | --: | --- |
| k | `K` | Key. |
| v | `V` | Value. |
