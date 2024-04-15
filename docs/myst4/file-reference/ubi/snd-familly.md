# `snd::Familly`

- [`UbiResourceType`](./index.md#ubiresourcetype-string): `"snd::Familly"`

## `snd::Familly` structure

| Name | Type | Condition |
| :-- | :-- | :-- |
| name | [`BasicString`](../base.md#basicstring-structure) |  |
| soundList | [`snd::SoundList`](./snd-soundlist.md) |  |
| pickerType | `uint32` |  |
| syncOnFamilly | `bool` |  |
| syncOnFamillyName | [`BasicString`](../base.md#basicstring-structure) | `syncOnFamilly` |
| initVolume | [`ValidatedUbiSubResource`](./index.md#validatedubisubresource-structure) [^1] |  |
| initNLoops | [`ValidatedUbiSubResource`](./index.md#validatedubisubresource-structure) [^2] |  |
| initWaitTimeBegin | [`ValidatedUbiSubResource`](./index.md#validatedubisubresource-structure) [^1] | `version >= 0x4` |
| initWaitTime | [`ValidatedUbiSubResource`](./index.md#validatedubisubresource-structure) [^1] |  |
| initWaitTimeEnd | [`ValidatedUbiSubResource`](./index.md#validatedubisubresource-structure) [^1] | `version >= 0x4` |
| rules | [`Array`](../base.md#array-structure)<[`UbiSubResource`](./index.md#ubisubresource-structure)> [^3] |  |

[^1]: If `isValid`, Revelation assumes `type` to be one of the [`"snd::InitValue"`](./snd-initvalue.md) types with a `float32` value type.
[^2]: If `isValid`, Revelation assumes `type` to be one of the [`"snd::InitValue"`](./snd-initvalue.md) types with a `int32` value type.
[^3]: Revelation assumes all `type` to be one of [`snd::FamillyPlaying` or `snd::FamillyPlayingSound`](#sndfamillyplaying-sndfamillyplayingsound-structure).

## `snd::FamillyPlaying` / `snd::FamillyPlayingSound` structure

It is unknown what the distinction is between `snd::FamillyPlaying` and `snd::FamillyPlayingSound`; they share the same serialisation routine.

| Name | Type |
| :-- | :-- |
| condition | `bool` |
| famillyName | [`BasicString`](../base.md#basicstring-structure) |
