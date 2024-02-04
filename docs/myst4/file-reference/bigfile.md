# BigFile

BigFile is the container format employed by Ubisoft for Revelation. All of Revelation's data is contained in BigFiles.

coderjo wrote [some Python scripts](https://github.com/coderjo/myst4tools) for manipulating BigFiles.

BigFiles are little-endian, and have the .m4b file extension.

## `BigFile` structure

| Name | Type | Description |
| :-- | --: | --- |
| magic | [`BasicString`](./base.md#basicstring-structure) | BigFile magic signature. Must be "UBI_BF_SIG\0". |
| version | `uint32` | Must be `1`. No other version is known. |
| root | [`FatDirectory`](#fatdirectory-structure) | Root directory entry. `root.name` must be empty. |
| fileTable | ... | Table of files described in `root`. |

## `FatDirectory` structure

Describes a single directory contained in a BigFile.

| Name | Type | Description |
| :-- | --: | --- |
| name | [`BasicString`](./base.md#basicstring-structure) | Directory name. In source material, all directory names have a redundant null-terminator if not empty. |
| nSubDirs | `uint8` | Number of sub-directories. |
| subDirs | [`FatDirectory`](#fatdirectory-structure)`[nSubDirs]` | Sub-directories. |
| files | [`Array`](./base.md#arrayt-structure)<[`FatFile`](#fatfile-structure)> |  |

## `FatFile` structure

Describes a single file contained in a BigFile.

| Name | Type | Description |
| :-- | --: | --- |
| name | [`BasicString`](./base.md#basicstring-structure) | File name. In source material, all file names have a redundant null-terminator if not empty. |
| size | `uint32` | File size. |
| pos | `uint32` | File's absolute start position in its containing BigFile. |
