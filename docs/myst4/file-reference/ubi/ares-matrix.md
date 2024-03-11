# `ares::Matrix`

An `ares::Matrix` contains a single [`Matrix44`](../base.md#matrix44-structure).

[`UbiResourceType`](./index.md#ubiresourcetype-string): `"ares::Matrix"`

## `ares::Matrix` structure

| Name | Type | Condition | Description |
| :-- | --: | :-- | --- |
| name | [`BasicString`](../base.md#basicstring-structure) | `ver >= 5` | Instance name. |
| matrix | [`Matrix44`](../base.md#matrix44-structure) |  | Matrix. |