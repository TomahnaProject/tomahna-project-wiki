# `CommandBlock`

A `CommandBlock` contains commands to be executed upon some AI event.

[`ThorResourceType`](./index.md#thorresourcetype-enum): `0x6`

Max. version: `0x1`

## `CommandBlock` structure

| Name | Type | Description |
| :-- | --: | --- |
| hdr | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) | Header. |
| cmds | [`Array`](../base.md#arrayt-structure)<[`EncryptedString`](../base.md#encryptedstring-structure)> | Commands. |
