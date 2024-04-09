# `ContainerResource`

- [`ThorResourceType`](./index.md#thorresourcetype-enum): `0x7`
- Max. version: `0x1`

A `ContainerResource` groups multiple resources together.

## `ContainerResource` structure

| Name | Type |
| :-- | :-- |
| header | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) |
| children | [`Array`](../base.md#array-structure)<[`ThorResource`](./index.md#thorresource-structure)> |
