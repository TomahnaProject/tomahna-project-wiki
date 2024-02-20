# Base types

## `FileMagic` string

With some exceptions, all asset files have a `FileMagic` at the start of the file. It can be one of `"ubi/b0-l"` and `"ubi/b0-b"`, which indicate whether the file is little- or big-endian respectively. However, only `"ubi/b0-l"` has ever been observed in the wild.

## `BasicString` structure

The basic UTF-16 string used all over the place. Sometimes referred to as `ubistring`.

| Name | Type | Description |
| :-- | --: | --- |
| len | `uint32` | Length of the string. |
| s | `char[len]` | The string. |

## `BasicWString` structure

Same as [`BasicString`](#basicstring-structure), except with UTF-16 encoding.

| Name | Type | Description |
| :-- | --: | --- |
| len | `uint32` | Length of the string. |
| s | `wchar_t[len]` | The string. |

## `Vector2` structure

Sometimes referred to as `vec2`.

| Name | Type | Description |
| :-- | --: | --- |
| x | `float` |  |
| y | `float` |  |

## `Vector3` structure

Sometimes referred to as `vec3`.

| Name | Type | Description |
| :-- | --: | --- |
| x | `float` |  |
| y | `float` |  |
| z | `float` |  |

## `Vector4` structure

Sometimes referred to as `vec4` or `quat`.

| Name | Type | Description |
| :-- | --: | --- |
| x | `float` |  |
| y | `float` |  |
| z | `float` |  |
| w | `float` |  |

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
| x | [`Vector4`](#vector4-structure) |  |
| y | [`Vector4`](#vector4-structure) |  |
| z | [`Vector4`](#vector4-structure) |  |
| w | [`Vector4`](#vector4-structure) |  |

## `Array`<`T`> structure

| Name | Type | Description |
| :-- | --: | --- |
| len | `uint32` | Length of the array. |
| elements | `T[len]` | Elements of the array. |

## `PairArray`<`K`, `V`> structure

| Name | Type | Description |
| :-- | --: | --- |
| len | `uint32` | Length of the array. |
| elements | [`Pair`](#pairk-v-structure)<`K`, `V`>`[len]` | Elements of the array. |

### `Pair`<`K`, `V`> structure

| Name | Type | Description |
| :-- | --: | --- |
| k | `K` | Key. |
| v | `V` | Value. |
