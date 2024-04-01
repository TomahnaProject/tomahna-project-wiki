# `ares::Matrix`

- [`UbiResourceType`](./index.md#ubiresourcetype-string): `"ares::Matrix"`

An `ares::Matrix` contains a single [`Matrix44`](../base.md#matrix44-structure).

## `ares::Matrix` structure

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| name | [`BasicString`](../base.md#basicstring-structure) | `ver >= 0x5` | Instance name. |
| matrix | [`Matrix44`](../base.md#matrix44-structure) |  | Matrix. |
