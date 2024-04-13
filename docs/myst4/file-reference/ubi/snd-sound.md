# `snd::Sound`

- [`UbiResourceType`](./index.md#ubiresourcetype-string): `"snd::Sound"`

## `snd::Sound` structure

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| name | [`BasicString`](../base.md#basicstring-structure) |  |  |
| soundID | `uint16` |  |  |
| groupID | `uint16` |  |  |
| defaultSetting | [`snd::Setting`](./snd-sound.md) |  |  |
| nSettings | `uint32` |  |  |
| type | `uint32` |  |  |
| volumeLine | `int32` | `version >= 0x3` |  |
| settings | [`Pair`](../base.md#pair-structure)<[`Context`](#context-structure), [`snd::Setting`](./snd-sound.md)>[`nSettings`] |  |  |

### `Context` structure

| Name | Type |
| :-- | :-- |
| world | `uint8` |
| zone | `uint8` |
| node | `uint16` |
