# Revelation Archives

## Archive

Revelation makes use of .m4b that are really Ubisoft's BigFile Game Data Archive format.

[From CoderJo](https://gist.github.com/coderjo/86968bfd3c17e6f7c3ecffd76c3482fa)

Endian order: little endian

### FILE HEADER

|  Type  | Count | Description |
| :----- | ----: | :---------- |
| uint32 |  0x1  | Signature string length = 0x0b |
| char   |  0xb  | Signature string = "UBI_BF_SIG" + 0x0 |
| uint32 |  0x1  | file format version? = 0x1 |
| uint32 |  0x1  | unknown = 0x0|
| DIR    |  0x1  | Root directory entry |
| DATA   |  ??   | Determined by file entries. can actually contain "slack space" |

### DIR structure

|  TYPE    | Count | Description |
| :-----   | ----: | :---------- |
| uint8    | 0x01  | Number of subdirectories (call this "sd") |
| DIRINFO  | sd    | Directory information structures for all subdirectories |
| uint32   | 0x01  | Number of files in this directory (call this "fc") |
| FILEINFO | fc    | File information structures |

### DIRINFO structure

|  Type  | Count | Description |
| :----- | ----: | :---------- |
| uint32 | 0x01  | Directory name length (dnl) |
| char   | dnl   | Directory name (null terminated, counted in dnl) |
| DIR    | 0x01  | Directory contents struct |

### FILEINFO structure

|  Type  | Count | Description |
| :----- | ----: | :---------- |
| uint32 | 0x01  | File name length (fnl) |
| char   | fnl   | File name (null terminated, counted in fnl) |
| uint32 | 0x01  | file length |
| uint32 | 0x01  | file offset (from start of m4b file) |

## Zap Files

A collection of multiple image files, generally 1 for color, 1 for transparency

    Partial Hex editor view of file back_01_03.zap in w1z01n020.m4b

    Header at 0x00000000
    20 00 00 00                        << header size
    02 00 00 00                        << maybe amount of channels? Never seen anything other than 2
    0a 00 00 00 0a 00 00 00            << ???

    a8 0c 00 00                        << length of jpg data for color
    52 0c 00 00                        << length of jpg data for alpha mask
    80 00 00 00 80 00 00 00            << width and height?

    Color data at 0x00000020
    ff d8 ff e0 00 10 4a 46 49 46 00   << beginning of JFIF data
    ...
    50 ab da 8f 40 3f ff d9            << end of JFIF data

    Alpha data at 0x00000cc8
    ff d8 ff e0 00 10 4a 46 49 46 00   << beginning of JFIF data
    ...
    8a ef 68 a2 8a 28 a2 bf ff d9      << end of JFIF data

    End of the file at 0x0000191a

## Sound Files

.s00
