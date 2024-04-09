# `CommandBlock`

- [`ThorResourceType`](./index.md#thorresourcetype-enum): `0x6`
- Max. version: `0x1`

A `CommandBlock` contains commands to be executed upon some AI event.

## `CommandBlock` structure

| Name | Type |
| :-- | :-- |
| header | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) |
| commands | [`Array`](../base.md#array-structure)<[`EncryptedString`](../base.md#encryptedstring-structure)> |
