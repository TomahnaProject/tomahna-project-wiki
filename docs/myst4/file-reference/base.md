# Base types

## `BasicString`

The basic UTF-16 string used all over the place. Sometimes referred to as `ubistring`.

| Name | Type | Description |
| :-- | --: | --- |
| len | `uint32` | Length of the string. |
| s | `char[len]` | The string. |

## `BasicWString`

Same as [`BasicString`](#basicstring), except with UTF-16 encoding.

| Name | Type | Description |
| :-- | --: | --- |
| len | `uint32` | Length of the string. |
| s | `wchar_t[len]` | The string. |

## `Vector2`

Sometimes referred to as `vec2`.

| Name | Type | Description |
| :-- | --: | --- |
| x | `float` |  |
| y | `float` |  |

## `Vector3`

Sometimes referred to as `vec3`.

| Name | Type | Description |
| :-- | --: | --- |
| x | `float` |  |
| y | `float` |  |
| z | `float` |  |

## `Vector4`

Sometimes referred to as `vec4` or `quat`.

| Name | Type | Description |
| :-- | --: | --- |
| x | `float` |  |
| y | `float` |  |
| z | `float` |  |
| w | `float` |  |

## `Matrix22`

| Name | Type | Description |
| :-- | --: | --- |
| x | [`Vector2`](#vector2) |  |
| y | [`Vector2`](#vector2) |  |

## `Matrix33`

| Name | Type | Description |
| :-- | --: | --- |
| x | [`Vector3`](#vector3) |  |
| y | [`Vector3`](#vector3) |  |
| z | [`Vector3`](#vector3) |  |

## `Matrix44`

| Name | Type | Description |
| :-- | --: | --- |
| x | [`Vector4`](#vector4) |  |
| y | [`Vector4`](#vector4) |  |
| z | [`Vector4`](#vector4) |  |
| w | [`Vector4`](#vector4) |  |

## `Array<T>`

| Name | Type | Description |
| :-- | --: | --- |
| len | `uint32` | Length of the array. |
| elements | `T[len]` | Elements of the array. |

## `PairArray<K, V>`

| Name | Type | Description |
| :-- | --: | --- |
| len | `uint32` | Length of the array. |
| elements | [`Pair<K, V>[len]`](#pairk-v) | Elements of the array. |

### `Pair<K, V>`

| Name | Type | Description |
| :-- | --: | --- |
| k | `K` | Key. |
| v | `V` | Value. |
