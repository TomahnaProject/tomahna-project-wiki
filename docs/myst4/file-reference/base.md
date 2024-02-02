# Base types

## `BasicString`

The basic UTF-16 string used all over the place. Sometimes referred to as `ubistring`.

| Name | Type | Count | Description |
| :-- | :-- | --: | --- |
| len | `uint32` | `0x1` | Length of the string. |
| s | `char` | len | The string. |

## `BasicWString`

Same as [`BasicString`](#basicstring), except with UTF-16 encoding.

| Name | Type | Count | Description |
| :-- | :-- | --: | --- |
| len | `uint32` | `0x1` | Length of the string. |
| s | `wchar_t` | len | The string. |

## `Vector2`

Sometimes referred to as `vec2`.

| Name | Type | Count | Description |
| :-- | :-- | --: | --- |
| x | `float` | `0x1` |  |
| y | `float` | `0x1` |  |

## `Vector3`

Sometimes referred to as `vec3`.

| Name | Type | Count | Description |
| :-- | :-- | --: | --- |
| x | `float` | `0x1` |  |
| y | `float` | `0x1` |  |
| z | `float` | `0x1` |  |

## `Vector4`

Sometimes referred to as `vec4`.

| Name | Type | Count | Description |
| :-- | :-- | --: | --- |
| x | `float` | `0x1` |  |
| y | `float` | `0x1` |  |
| z | `float` | `0x1` |  |
| w | `float` | `0x1` |  |

## `Matrix22`

| Name | Type | Count | Description |
| :-- | :-- | --: | --- |
| x | [`Vector2`](#vector2) | `0x1` |  |
| y | [`Vector2`](#vector2) | `0x1` |  |

## `Matrix33`

| Name | Type | Count | Description |
| :-- | :-- | --: | --- |
| x | [`Vector3`](#vector3) | `0x1` |  |
| y | [`Vector3`](#vector3) | `0x1` |  |
| z | [`Vector3`](#vector3) | `0x1` |  |

## `Matrix44`

| Name | Type | Count | Description |
| :-- | :-- | --: | --- |
| x | [`Vector4`](#vector4) | `0x1` |  |
| y | [`Vector4`](#vector4) | `0x1` |  |
| z | [`Vector4`](#vector4) | `0x1` |  |
| w | [`Vector4`](#vector4) | `0x1` |  |

## `Quaternion`

TODO

## `Array<T>`

| Name | Type | Count | Description |
| :-- | :-- | --: | --- |
| len | `uint32` | `0x1` | Length of the array. |
| elements | `T` | len | Elements of the array. |

## `PairArray<K, V>`

| Name | Type | Count | Description |
| :-- | :-- | --: | --- |
| len | `uint32` | `0x1` | Length of the array. |
| elements | [`Pair<K, V>`](#pairk-v) | len | Elements of the array. |

### `Pair<K, V>`

| Name | Type | Count | Description |
| :-- | :-- | --: | --- |
| k | `K` | `0x1` | Key. |
| v | `V` | `0x1` | Value. |
