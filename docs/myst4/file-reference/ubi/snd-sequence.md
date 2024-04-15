# `snd::Sequence`

- [`UbiResourceType`](./index.md#ubiresourcetype-string): `"snd::Sequence"`

`snd::Sequence` resources are exclusively contained in `.seq` files found in `sound.m4b/sequence/`.

## `snd::Sequence` structure

| Name | Type |
| :-- | :-- |
| name | [`BasicString`](../base.md#basicstring-structure) |
| initVolume | [`ValidatedUbiSubResource`](./index.md#validatedubisubresource-structure) [^1] |
| initNLoops | [`ValidatedUbiSubResource`](./index.md#validatedubisubresource-structure) [^2] |
| initSpeedFactor | [`ValidatedUbiSubResource`](./index.md#validatedubisubresource-structure) [^1] |
| sounds | [`Array`](../base.md#array-structure)<[`UbiSubResource`](./index.md#ubisubresource-structure)> [^3] |
| famillies | [`Array`](../base.md#array-structure)<[`UbiSubResource`](./index.md#ubisubresource-structure)> [^4] |

[^1]: If `isValid`, Revelation assumes `type` to be one of the [`"snd::InitValue"`](./snd-initvalue.md) types with a `float32` value type.
[^2]: If `isValid`, Revelation assumes `type` to be one of the [`"snd::InitValue"`](./snd-initvalue.md) types with a `int32` value type.
[^3]: Revelation assumes all `type` to be [`snd::Sound`](./snd-sound.md).
[^4]: Revelation assumes all `type` to be [`snd::Familly`](./snd-familly.md).
