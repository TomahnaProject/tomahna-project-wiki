# Base types

## `FileMagic` string

With some exceptions, all asset files have a `FileMagic` at the start of the file. It can be one of `"ubi/b0-l"` and `"ubi/b0-b"`, which indicate whether the file is little- or big-endian respectively. However, only `"ubi/b0-l"`, the little-endian variant, has ever been observed in the wild.

## `BasicString` structure

The basic UTF-16 string used all over the place. Sometimes referred to as `ubistring`.

| Name | Type | Description |
| :-- | :-- | --- |
| len | `uint32` | Length of the string. |
| s | `char`\[`len`\] | The string. |

## `BasicWString` structure

Same as [`BasicString`](#basicstring-structure), except with UTF-16 encoding.

| Name | Type | Description |
| :-- | :-- | --- |
| len | `uint32` | Length of the string. |
| s | `wchar_t`\[`len`\] | The string. |

## `EncryptedString` structure

Same as [`BasicString`](#basicstring-structure), except all `char`s are "swizzled".

| Name | Type | Description |
| :-- | :-- | --- |
| len | `uint32` | Length of the string. |
| s | `char`\[`len`\] | The string. |

Swizzle/unswizzle:

```c++
void EncryptedString::Swizzle() {
    for (int i = 0; i < this->len; i++) {
        byte b = this->s[i];
        this->s[i] = (b & 0xAA) >> 1 | (b & 0x55) << 1;
    }
    return;
}
```

## `Vector2` structure

Sometimes referred to as `vec2`.

| Name | Type |
| :-- | :-- |
| x | `float32` |
| y | `float32` |

## `Vector3` structure

Sometimes referred to as `vec3`.

| Name | Type |
| :-- | :-- |
| x | `float32` |
| y | `float32` |
| z | `float32` |

## `Vector4` / `Quaternion` structure

Sometimes referred to as `vec4` or `quat` respectively.

| Name | Type |
| :-- | :-- |
| x | `float32` |
| y | `float32` |
| z | `float32` |
| w | `float32` |

## `Matrix22` structure

| Name | Type |
| :-- | :-- |
| x | [`Vector2`](#vector2-structure) |
| y | [`Vector2`](#vector2-structure) |

## `Matrix33` structure

| Name | Type |
| :-- | :-- |
| x | [`Vector3`](#vector3-structure) |
| y | [`Vector3`](#vector3-structure) |
| z | [`Vector3`](#vector3-structure) |

## `Matrix44` structure

| Name | Type |
| :-- | :-- |
| x | [`Vector4`](#vector4-quaternion-structure) |
| y | [`Vector4`](#vector4-quaternion-structure) |
| z | [`Vector4`](#vector4-quaternion-structure) |
| w | [`Vector4`](#vector4-quaternion-structure) |

## `Color` structure

| Name | Type | Description |
| :-- | :-- | --- |
| r | `float32` | Red. |
| g | `float32` | Green. |
| b | `float32` | Blue. |
| a | `float32` | Alpha. |

## `Box` structure

| Name | Type |
| :-- | :-- |
| pMin | [`Vector3`](#vector3-structure) |
| pMax | [`Vector3`](#vector3-structure) |

## `Plane` structure

| Name | Type |
| :-- | :-- |
| normal | [`Vector3`](#vector3-structure) |
| constant | `float32` |

## `Array`<`Type`> structure {#array-structure}

| Name | Type | Description |
| :-- | :-- | --- |
| len | `uint32` | Length of the array. |
| elements | `Type`\[`len`\] | Elements of the array. |

## `PairArray`<`Key`, `Value`> structure {#pairarray-structure}

| Name | Type | Description |
| :-- | :-- | --- |
| len | `uint32` | Length of the array. |
| elements | [`Pair`](#pair-structure)<`Key`, `Value`>\[`len`\] | Elements of the array. |

### `Pair`<`Key`, `Value`> structure {#pair-structure}

| Name | Type | Description |
| :-- | :-- | --- |
| k | `Key` | Key. |
| v | `Value` | Value. |

## `CompressedQuaternion3U16` structure

| Name | Type |
| :-- | :-- |
| x | `uint16` |
| y | `uint16` |
| z | `uint16` |

Compression/decompression:

```c++
void CompressedQuaternion3U16::Compress(Quaternion *src) {
    if (src->w < 0.0) {
        this->x = (uint16)((1.0 - src->x) * 32767.0);
        this->y = (uint16)((1.0 - src->y) * 32767.0);
        this->z = (uint16)((1.0 - src->z) * 32767.0);
    } else {
        this->x = (uint16)((1.0 + src->x) * 32767.0);
        this->y = (uint16)((1.0 + src->y) * 32767.0);
        this->z = (uint16)((1.0 + src->z) * 32767.0);
    }
    return;
}

void CompressedQuaternion3U16::Decompress(Quaternion *dst) {
    float w;

    dst->x = (float32)this->x*(1.0/32767.0) - 1.0;
    dst->y = (float32)this->y*(1.0/32767.0) - 1.0;
    dst->z = (float32)this->z*(1.0/32767.0) - 1.0;
    w = ((1.0 - dst->x*dst->x) - dst->y*dst->y) - dst->z*dst->z;
    if (w > 0.0) {
        dst->w = sqrt(w);
    } else {
        dst->w = 0.0;
    }
    return;
}
```

## `CompressedQuaternionU32` type

- Type: `uint32`
- Bits: `xxaaaaaa aaaabbbb bbbbbbcc cccccccc`
    - `xx`: greatest quat element (0 = `x`, 1 = `y`, 2 = `z`, 3 = `w`).
    - `aaaaaaaaaa`/`bbbbbbbbbb`/`cccccccccc`: other three elements.

Compression/decompression:

```c++
const float32 oneOverRootTwo  = sqrt(2.0) /     2.0;
const float32 scaleRange10Bit = sqrt(2.0) / pow(2.0, 10);

static uint32 CompressedQuaternionU32::CompressElement(float32 elem) {
    return min((uint32)((elem + oneOverRootTwo) * (1.0/scaleRange10Bit) + 0.000025), 0x3FF);
}

void CompressedQuaternionU32::Compress(Quaternion *src) {
    uint32 a, b, c, x;
    float32 ax, ay, az, aw;
    Quaternion q;

    q = *src;
    q.Normalize();

    ax = abs(q.x);
    ay = abs(q.y);
    az = abs(q.z);
    aw = abs(q.w);

    if (ax > ay && ax > az && ax > aw) {
        // x is greatest element.
        if (q.x < 0.0) q.Negate();
        a = CompressElement(q.y);
        b = CompressElement(q.z);
        c = CompressElement(q.w);
        x = 0;
    } else if (ay > az && ay > aw) {
        // y is greatest element.
        if (q.y < 0.0) q.Negate();
        a = CompressElement(q.x);
        b = CompressElement(q.z);
        c = CompressElement(q.w);
        x = 1;
    } else if (az > aw) {
        // z is greatest element.
        if (q.z < 0.0) q.Negate();
        a = CompressElement(q.x);
        b = CompressElement(q.y);
        c = CompressElement(q.w);
        x = 2;
    } else {
        // w is greatest element.
        if (q.w < 0.0) q.Negate();
        a = CompressElement(q.x);
        b = CompressElement(q.y);
        c = CompressElement(q.z);
        x = 3;
    }

    this->v = (x << 30) | (a << 20) | (b << 10) | c;
    return;
}

void CompressedQuaternionU32::Decompress(Quaternion *dst) {
    float32 a, b, c, s;

    a = (float32)(this->v >> 20 & 0x3FF) * scaleRange10Bit - oneOverRootTwo;
    b = (float32)(this->v >> 10 & 0x3FF) * scaleRange10Bit - oneOverRootTwo;
    c = (float32)(this->v >>  0 & 0x3FF) * scaleRange10Bit - oneOverRootTwo;
    s = sqrt(((1.0 - a*a) - b*b) - c*c);

    switch this->v >> 30 {
    case 0:
        dst->x = s;
        dst->y = a;
        dst->z = b;
        dst->w = c;
        break;
    case 1:
        dst->x = a;
        dst->y = s;
        dst->z = b;
        dst->w = c;
        break;
    case 2:
        dst->x = a;
        dst->y = b;
        dst->z = s;
        dst->w = c;
        break;
    case 3:
        dst->x = a;
        dst->y = b;
        dst->z = c;
        dst->w = s;
        break;
    }
    return;
}
```
