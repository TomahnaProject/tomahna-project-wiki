# `MORE::Clip`

- [`UbiResourceType`](./index.md#ubiresourcetype-string): `"MORE::Animation"`

TODO

## `MORE::Clip` structure

| Name | Type | Description | Description |
| :-- | :-- | :-- | --- |
| type | `uint32` |  |  |
| layerID | `uint16` |  |  |
| isLooping | `bool` |  |  |
| timeScale | `float32` |  |  |
| blending | `float32` | `ver >= 0x1` |  |
| transitionIn | `float32` | `ver >= 0x1` |  |
| transitionOut | `float32` | `ver >= 0x1` |  |
| timeWarpOn | `bool` | `ver >= 0xE` |  |
| timeWarp | [`LinearWarp01`](#linearwarp01-structure) | `ver >= 0xE && timeWarpOn` |  |
| animationData | [`SimpleAnim`](#simpleanim-structure) | `type == 0x0` |  |
| animationData | [`SyncAnims`](#syncanims-structure) | `type == 0x1` |  |

!!! note
    If `type` is not 0 or 1, Revelation will crash.

## `LinearWarp01` structure

| Name | Type | Description |
| :-- | :-- | --- |
| ??? | [`Array`](../base.md#array-structure)<[`LinearWarp01Unknown`](#linearwarp01unknown-structure)> |  |

### `LinearWarp01Unknown` structure

| Name | Type | Description |
| :-- | :-- | --- |
| first | `float32` |  |
| second | `float32` |  |

## `SimpleAnim` structure

| Name | Type | Description |
| :-- | :-- | --- |
| animation | [`UbiSubResource`](./index.md#ubisubresource-structure) | Revelation assumes `data.type` to be `"MORE::Animation"`. |

## `SyncAnims` structure

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| subLayers | [`Array`](../base.md#array-structure)<[`UbiSubResource`](./index.md#ubisubresource-structure)> |  | Revelation assumes all `data.type` to be `"MORE::Animation"`. |
| blendings | `float32`[`subLayers.len`] | `ver >= 0x1` |  |
| adjustDurations | `bool`[`subLayers.len`] | `ver >= 0xB` |  |

!!! note
    Any `subLayers` values which have an `instants.len` which does not match the first layer's, are ignored, along with their corresponding `blendings` and `adjustDurations` values.
