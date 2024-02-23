# `ContainerResource`

A `ContainerResource` groups multiple resources together.

[`ThorResourceType`](./index.md#thorresourcetype-enum): `0x7`

## `ContainerResource` structure

| Name | Type | Description |
| :-- | --: | --- |
| hdr | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) | Header. |
| children | [`Array`](../base.md#arrayt-structure)<[`ThorResource`](./index.md#thorresource-structure)> | Children. |
