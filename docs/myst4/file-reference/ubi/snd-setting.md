# `snd::Setting`

- [`UbiResourceType`](./index.md#ubiresourcetype-string): `"snd::Setting"`

## `snd::Setting` structure

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| volume | [`ValidatedUbiSubResource`](./index.md#validatedubisubresource-structure) [^1] |  |  |
| fadeIn | [`ValidatedUbiSubResource`](./index.md#validatedubisubresource-structure) [^1] |  |  |
| fadeInCurve | `uint32` |  |  |
| fadeOut | [`ValidatedUbiSubResource`](./index.md#validatedubisubresource-structure) [^1] |  |  |
| fadeOutCurve | `uint32` |  |  |
| pitch | [`ValidatedUbiSubResource`](./index.md#validatedubisubresource-structure) [^1] |  |  |
| nLoops | [`ValidatedUbiSubResource`](./index.md#validatedubisubresource-structure) [^2] | `version < 3` | If `x = nLoops.Get(), x < 501`, this field is converted to [`snd::InitValueConst`]<`int32`> with `nLoops.const = x`. Otherwise, this field is set to `NULL`. |
| nLoops | [`ValidatedUbiSubResource`](./index.md#validatedubisubresource-structure) [^3] | `version >= 3` |  |
| panning | [`ValidatedUbiSubResource`](./index.md#validatedubisubresource-structure) [^4] |  |  |
| position | [`ValidatedUbiSubResource`](./index.md#validatedubisubresource-structure) [^5] |  |  |
| behaviour | `int32` |  |  |

[^1]: If `isValid`, Revelation assumes `type` to be one of the [`"snd::InitValue"`](./snd-initvalue.md) types with a `float32` value type.
[^2]: If `isValid`, Revelation assumes `type` to be one of the [`"snd::InitValue"`](./snd-initvalue.md) types with a `uint32` value type.
[^3]: If `isValid`, Revelation assumes `type` to be one of the [`"snd::InitValue"`](./snd-initvalue.md) types with a `int32` value type.
[^4]: If `isValid`, Revelation assumes `type` to be [`snd::VirtualPanning`](./snd-virtualpanning.md).
[^5]: If `isValid`, Revelation assumes `type` to be one of the [`"snd::InitValue"`](./snd-initvalue.md) types with a [`Vector3`](../base.md#vector3-structure) value type.
