# `TextResource`

- [`ThorResourceType`](./index.md#thorresourcetype-enum): `0x25`
- Max. version: `0x1`

A `TextResource` contains a collection of [`Text`](./text.md#text) resources, possibly nested in one or more child `TextResource`s.

## `TextResource` structure

| Name | Type | Description |
| :-- | :-- | --- |
| header | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) |  |
| ??? | `int32` | Revelation's code appears to ignore this field. Never observed to be anything other than `0x1`. |
| blip | [`Blip`](#blip-structure) | Root blip. |

### `Blip` structure

Under the hood a `Blip` is really just a [`TextResource`](#textresource) without `header` and the unknown `int32`.

| Name | Type |
| :-- | :-- |
| nTexts | `int32` |
| nGroups | `int32` |
| texts | [`BlipText`](#bliptext-structure)\[`nTexts`\] |
| groups | [`BlipGroup`](#blipgroup-structure)\[`nGroups`\] |

#### `BlipText` structure

| Name | Type | Description |
| :-- | :-- | --- |
| resName | [`BasicString`](../base.md#basicstring-structure) | [`Text`](./text.md#text) resource name. |
| text | [`Text`](./text.md) |  |

#### `BlipGroup` structure

| Name | Type | Description |
| :-- | :-- | --- |
| resName | [`BasicString`](../base.md#basicstring-structure) | [`TextResource`](#textresource) resource name. |
| group | [`Blip`](#blip-structure) |  |
