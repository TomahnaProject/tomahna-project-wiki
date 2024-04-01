# `TextResource`

- [`ThorResourceType`](./index.md#thorresourcetype-enum): `0x25`
- Max. version: `0x1`

A `TextResource` contains a collection of [`Text`](./text.md#text) resources, possibly nested in one or more child `TextResource`s.

## `TextResource` structure

| Name | Type | Description |
| :-- | :-- | --- |
| hdr | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) | Header. |
| ??? | `int32` | Revelation's code appears to ignore this field. Never observed to be anything other than `0x1`. |
| blip | [`Blip`](#blip-structure) | Root blip. |

### `Blip` structure

Under the hood a `Blip` is really just a [`TextResource`](#textresource) without the header and unknown `int32`.

| Name | Type | Description |
| :-- | :-- | --- |
| nTexts | `int32` | Number of texts. |
| nGroups | `int32` | Number of groups. |
| texts | [`BlipText`](#bliptext-structure)\[`nTexts`\] | Texts. |
| groups | [`BlipGroup`](#blipgroup-structure)\[`nGroups`\] | Groups. |

#### `BlipText` structure

| Name | Type | Description |
| :-- | :-- | --- |
| resName | [`BasicString`](../base.md#basicstring-structure) | [`Text`](./text.md#text) resource name. |
| text | [`Text`](./text.md) | Child text. |

#### `BlipGroup` structure

| Name | Type | Description |
| :-- | :-- | --- |
| resName | [`BasicString`](../base.md#basicstring-structure) | [`TextResource`](#textresource) resource name. |
| group | [`Blip`](#blip-structure) | Child group. |
