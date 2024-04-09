# BigFile

BigFile is the container format employed by Ubisoft for Revelation. All of Revelation's data is contained in BigFiles.

coderjo wrote [some Python scripts](https://github.com/coderjo/myst4tools) for manipulating BigFiles.

BigFiles are little-endian, and have the .m4b file extension.

## `BigFile` structure

| Name | Type | Description |
| :-- | :-- | --- |
| magic | [`BasicString`](./base.md#basicstring-structure) | Magic signature. Must be `"UBI_BF_SIG\0"`. |
| version | `uint32` | Must be `0x1`. No other version is known. |
| root | [`FatDirectory`](#fatdirectory-structure) | `root.name` must be empty. |
| fileTable | ... | Table of files described in `root`. |

## `FatDirectory` structure

Describes a single directory contained in a BigFile.

| Name | Type | Description |
| :-- | :-- | --- |
| name | [`BasicString`](./base.md#basicstring-structure) | In source material, all non-empty directory names have a redundant null-terminator. |
| nSubDirs | `uint8` |  |
| subDirs | [`FatDirectory`](#fatdirectory-structure)\[`nSubDirs`\] |  |
| files | [`Array`](./base.md#array-structure)<[`FatFile`](#fatfile-structure)> |  |

## `FatFile` structure

Describes a single file contained in a BigFile.

| Name | Type | Description |
| :-- | :-- | --- |
| name | [`BasicString`](./base.md#basicstring-structure) | In source material, all non-empty file names have a redundant null-terminator. |
| size | `uint32` |  |
| pos | `uint32` | File's absolute start position in its containing BigFile. |
