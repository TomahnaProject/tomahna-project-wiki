# `VariableResource`

- [`ThorResourceType`](./index.md#thorresourcetype-enum): `0x28`
- Max. version: `0x1`

A `VariableResource` contains the value of a variable.

## `VariableResource` structure

| Name | Type | Condition |
| :-- | :-- | :-- |
| header | [`ThorResourceHeader`](./index.md#thorresourceheader-structure) |  |
| type | `uint32` |  |
| value | `uint8` | `type == 0x1` |
| value | `uint16` | `type == 0x2` |
| value | `uint32` | `type == 0x3` |
| value | `int8` | `type == 0x4` |
| value | `int16` | `type == 0x5` |
| value | `int32` | `type == 0x6` |
| value | `float32` | `type == 0x7` |
| value | `float64` | `type == 0x8` |
| value | `bool` | `type == 0x9` |
| value | [`BasicString`](../base.md#basicstring-structure) | `type == 0xA` |
| value | [`Vector3`](../base.md#vector3-structure) | `type == 0xB` |
