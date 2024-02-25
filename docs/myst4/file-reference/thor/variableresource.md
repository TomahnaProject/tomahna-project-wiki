# `VariableResource`

A `VariableResource` contains the value of a variable.

[`ThorResourceType`](./index.md#thorresourcetype-enum): `0x28`

Max. version: `0x1`

## `VariableResource` structure

| Name | Type | Condition | Description |
| :-- | --: | :-- | --- |
| hdr | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) |  | Header. |
| type | `uint32` |  | Type. |
| v | `uint8` | `type == 0x1` | Value. |
| v | `uint16` | `type == 0x2` | Value. |
| v | `uint32` | `type == 0x3` | Value. |
| v | `int8` | `type == 0x4` | Value. |
| v | `int16` | `type == 0x5` | Value. |
| v | `int32` | `type == 0x6` | Value. |
| v | `float32` | `type == 0x7` | Value. |
| v | `float64` | `type == 0x8` | Value. |
| v | `bool` | `type == 0x9` | Value. |
| v | [`BasicString`](../base.md#basicstring-structure) | `type == 0xA` | Value. |
| v | [`Vector3`](../base.md#vector3-structure) | `type == 0xB` | Value. |
