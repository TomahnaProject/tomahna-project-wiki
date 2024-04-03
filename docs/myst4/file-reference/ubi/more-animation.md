# `MORE::Animation`

- [`UbiResourceType`](./index.md#ubiresourcetype-string): `"MORE::Animation"`

TODO

## `MORE::Animation` structure

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| name | [`BasicString`](../base.md#basicstring-structure) | `ver < 0xF` | Instance name. |
| duration | `float32` |  |  |
| isDelta | `bool` | `ver >= 0xC` |  |
| tracks | [`Array`](../base.md#array-structure)<[`Track`](#track-structure)> |  |  |
| instants | [`Array`](../base.md#array-structure)<[`Instant`](#instant-structure)> | `ver >= 0x9` |  |

### `Track` structure

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| type | `uint32` |  | Never observed to be `type >= 0x0D`. |
| name | [`BasicString`](../base.md#basicstring-structure) |  |  |
| data | [`TrackSimple`](#tracksimple-structure)<`uint16`, `uint16`, [`TimeF16`](#timef16-type)> | `type == 0x00` |  |
| data | [`TrackSimple`](#tracksimple-structure)<`float32`, `float32`, `float32`> | `type == 0x01` |  |
| data | [`TrackSimple`](#tracksimple-structure)<[`Vector3`](../base.md#vector3-structure), [`Vector3`](../base.md#vector3-structure), `float32`> | `type == 0x02` |  |
| data | [`TrackSimple`](#tracksimple-structure)<[`Quaternion`](../base.md#vector4-quaternion-structure), [`Quaternion`](../base.md#vector4-quaternion-structure), `float32`> | `type == 0x03` |  |
| data | [`TrackLinear`](#tracklinear-structure)<`float32`, `float32`, `float32`> | `type == 0x04` |  |
| data | [`TrackLinear`](#tracklinear-structure)<[`Vector3`](../base.md#vector3-structure), [`Vector3`](../base.md#vector3-structure), `float32`> | `type == 0x05` |  |
| data | [`TrackLinear`](#tracklinear-structure)<[`Quaternion`](../base.md#vector4-quaternion-structure), [`Quaternion`](../base.md#vector4-quaternion-structure), `float32`> | `type == 0x06` |  |
| data | [`TrackBezier`](#trackbezier-structure)<`float32`, `float32`, `float32`> | `type == 0x07` |  |
| data | [`TrackBezier`](#trackbezier-structure)<[`Vector3`](../base.md#vector3-structure), [`Vector3`](../base.md#vector3-structure), `float32`> | `type == 0x08` |  |
| data | [`TrackBezier`](#trackbezier-structure)<[`Quaternion`](../base.md#vector4-quaternion-structure), [`Quaternion`](../base.md#vector4-quaternion-structure), `float32`> | `type == 0x09` |  |
| data | [`TrackTCB`](#tracktcb-structure)<`float32`> | `type == 0x0A` |  |
| data | [`TrackTCB`](#tracktcb-structure)<[`Vector3`](../base.md#vector3-structure)> | `type == 0x0B` |  |
| data | [`TrackTCB`](#tracktcb-structure)<[`Quaternion`](../base.md#vector4-quaternion-structure)> | `type == 0x0C` |  |
| data | [`TrackDisplacement`](#trackdisplacement-structure) | `type == 0x0D` |  |
| data | [`TrackEvent`](#trackevent-structure) | `type == 0x0E` |  |
| data | [`TrackUser`](#trackuser-structure)<`uint16`> | `type == 0x0F` |  |
| data | [`TrackUser`](#trackuser-structure)<`float32`> | `type == 0x10` |  |
| data | [`TrackUser`](#trackuser-structure)<[`Vector3`](../base.md#vector3-structure)> | `type == 0x11` |  |
| data | [`TrackUser`](#trackuser-structure)<[`Quaternion`](../base.md#vector4-quaternion-structure)> | `type == 0x12` |  |
| data | [`TrackSimple`](#tracksimple-structure)<[`Quaternion`](../base.md#vector4-quaternion-structure), [`CompressedQuaternionU32`](../base.md#compressedquaternionu32-type), `float32`> | `type == 0x13` |  |
| data | [`TrackLinear`](#tracklinear-structure)<[`Quaternion`](../base.md#vector4-quaternion-structure), [`CompressedQuaternionU32`](../base.md#compressedquaternionu32-type), `float32`> | `type == 0x14` |  |
| data | [`TrackBezier`](#trackbezier-structure)<[`Quaternion`](../base.md#vector4-quaternion-structure), [`CompressedQuaternionU32`](../base.md#compressedquaternionu32-type), `float32`> | `type == 0x15` |  |
| data | [`TrackSimple`](#tracksimple-structure)<[`Quaternion`](../base.md#vector4-quaternion-structure), [`CompressedQuaternion3U16`](../base.md#compressedquaternion3u16-structure), [`TimeF16`](#timef16-type)> | `type == 0x18` |  |
| data | [`TrackLinear`](#tracklinear-structure)<[`Quaternion`](../base.md#vector4-quaternion-structure), [`CompressedQuaternion3U16`](../base.md#compressedquaternion3u16-structure), [`TimeF16`](#timef16-type)> | `type == 0x19` |  |
| data | [`TrackBezier`](#trackbezier-structure)<[`Quaternion`](../base.md#vector4-quaternion-structure), [`CompressedQuaternion3U16`](../base.md#compressedquaternion3u16-structure), [`TimeF16`](#timef16-type)> | `type == 0x1A` |  |
| data | [`TrackSimple`](#tracksimple-structure)<[`Vector3`](../base.md#vector3-structure), [`EulerAngleRad`](#euleranglerad-type), [`TimeF16`](#timef16-type)> | `type == 0x1D` |  |
| data | [`TrackLinear`](#tracklinear-structure)<[`Vector3`](../base.md#vector3-structure), [`EulerAngleRad`](#euleranglerad-type), [`TimeF16`](#timef16-type)> | `type == 0x1E` |  |
| data | [`TrackBezier`](#trackbezier-structure)<[`Vector3`](../base.md#vector3-structure), [`EulerAngleRad`](#euleranglerad-type), [`TimeF16`](#timef16-type)> | `type == 0x1F` |  |

!!! note
    Any other value for `type` will have Revelation crash.

#### `TimeF16` type

- Type: `uint16`

Compression/decompression:

```c++
uint16 TimeF16::Compress(float32 src) {
    return (uint16)((*src + 300.0) * (1.0/600.0) * 65534.0);
}

float32 TimeF16::Decompress(uint16 src) {
    return (float32)src * (1.0/65534.0) * 600.0 - 300.0;
}
```

#### `EulerAngleRad` type

- Type: `uint16`

Compression/decompression:

```c++
uint16 EulerAngleRad::Compress(float32 src) {
    return (uint16)((src + M_PI*10) * (M_PI*20) * 65534.0);
}

float32 EulerAngleRad::Decompress(uint16 src) {
    return (float32)src * (1.0/65534.0) * (1.0/(M_PI*20) - M_PI*10);
}
```

#### `TrackSimple`<`Value`, `ValueComp`, `Time`> structure {#tracksimple-structure}

| Name | Type | Description |
| :-- | :-- | --- |
| terminate | `bool` | Revelation's code appears to ignore this field. Never observed to be anything other than `true`. |
| keys | [`Array`](../base.md#array-structure)<[`KeySimple`](#keysimple-structure)<`Value`, `ValueComp`, `Time`>> | Keys. |

###### `KeySimple`<`Value`, `ValueComp`, `Time`> structure {#keysimple-structure}

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| time | `float32` | `ver < 0x10` |  |
| time | `Time` | `ver >= 0x10` |  |
| value | `ValueComp` |  |  |

#### `TrackLinear`<`Value`, `ValueComp`, `Time`> structure {#tracklinear-structure}

| Name | Type | Description |
| :-- | :-- | --- |
| terminate | `bool` | Revelation's code appears to ignore this field. Never observed to be anything other than `true`. |
| keys | [`Array`](../base.md#array-structure)<[`KeyLinear`](#keylinear-structure)<`Value`, `ValueComp`, `Time`>> | Keys. |

###### `KeyLinear`<`Value`, `ValueComp`, `Time`> structure {#keylinear-structure}

| Name | Type | Description |
| :-- | :-- | --- |
| time | `Time` |  |
| value | `ValueComp` |  |

#### `TrackBezier`<`Value`, `ValueComp`, `Time`> structure {#trackbezier-structure}

| Name | Type | Description |
| :-- | :-- | --- |
| terminate | `bool` | Revelation's code appears to ignore this field. Never observed to be anything other than `true`. |
| keys | [`Array`](../base.md#array-structure)<[`KeyBezier`](#keybezier-structure)<`Value`, `ValueComp`, `Time`>> | Keys. |

###### `KeyBezier`<`Value`, `ValueComp`, `Time`> structure {#keybezier-structure}

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| time | `Time` |  |  |
| value | `ValueComp` |  |  |
| derSrc | `Value` | `ver < 0x11` |  |
| derDst | `Value` | `ver < 0x11` | Ignored if `Value == Quaternion`. |
| derSrc | `ValueComp` | `ver >= 0x11` |  |
| derDst | `ValueComp` | `ver >= 0x11 && Value != Quaternion` |  |
| flatOut | `bool` |  |  |

#### `TrackTCB`<`Value`> structure {#tracktcb-structure}

| Name | Type | Description |
| :-- | :-- | --- |
| terminate | `bool` | Revelation's code appears to ignore this field. Never observed to be anything other than `true`. |
| keys | [`Array`](../base.md#array-structure)<[`KeyTCB`](#keytcb-structure)<`Value`>> | Keys. |

###### `KeyTCB`<`Value`> structure {#keytcb-structure}

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| time | `float32` |  |  |
| value | `Value` |  |  |
| tens | `float32` |  |  |
| cont | `float32` |  |  |
| bias | `float32` |  |  |
| easeTo | `float32` |  |  |
| easeFrom | `float32` |  |  |
| derSrc | `Value` |  |  |
| derDst | `Value` |  |  |
| angle | `float32` | `Value == Quaternion` |  |
| axis | [`Vector3`](../base.md#vector3-structure) | `Value == Quaternion` |  |

#### `TrackDisplacement` structure

| Name | Type | Description |
| :-- | :-- | --- |
| position | [`Track`](#track-structure) |  |
| rotation | [`Track`](#track-structure) |  |

#### `TrackEvent` structure

| Name | Type | Description |
| :-- | :-- | --- |
| keys | [`Array`](../base.md#array-structure)<[`KeyEvent`](#keyevent-structure)> | Keys. |

###### `KeyEvent` structure

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| time | `float32` |  |  |
| value | `uint32` |  |  |
| userData | [`BasicString`](../base.md#basicstring-structure) | `ver >= 0x2` |  |

#### `TrackUser`<`Value`> structure {#trackuser-structure}

| Name | Type | Description |
| :-- | :-- | --- |
| terminate | `bool` | Revelation's code appears to ignore this field. |

### `Instant` structure

| Name | Type | Description |
| :-- | :-- | --- |
| time | `float32` |  |
| id | `uint16` |  |
