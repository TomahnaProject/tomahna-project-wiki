# Music Sequencing

The music in Myst4 is similar to Myst3 in that it uses sequencing to compose many separate sound files dynamically into music so that the game can offer more variety when listening to the same piece for a long period of time compared to a fixed piece of music looped endlessly.

# Sequence Files

Each music track / cue has a sequence file (.seq) located within the sequence folder located within the main sound.m4b archive.
The game shipped with 48 files of these files (assuming no variation between versions).

:warning: **This page is a WIP**: Do not use it as gospel reference 

[Useful Hex Editor designed for Reverse Engineering](https://web.imhex.werwolv.net/)
[Useful Hex Conversion Tool](https://www.scadacore.com/tools/programming-calculators/online-hex-converter/)

Endian order: unknown - likely little endian

**FILE HEADER**

|  Type  | Count | Description |
| :----- | ----: | :---------- |
| char   |  0x8  | Header string "ubi/b0-l" |
| uint32 |  0x1  | unknown - family count? |


**SEQUENCE Structure**
| uint32 |  0x1  | Sequence prefix string length (spl) |
| char   |  spl  | Sequence prefix string |
| uint32 |  0x1  | Sequence name length (snl) |
| char   |  snl  | Sequence name |
| bool   |  0x1  | unknown |
| int32  |  0x1  | unknown |
| int32  |  0x1  | UbiDataType prefix string length (dpl1) |
| float  |  dpl1 | UbiDataType prefix string - one |
| int32  |  0x1  | UbiDataType prefix string length (dpl2) |
| int32  |  dpl2 | UbiDataType prefix string - two |
| int32  |  0x1  | UbiDataType prefix string length (dpl3) |
| float  |  dpl3 | UbiDataType prefix string - three |


**FAMILY Structure**
| int32  |  0x1  | unknown  |
| char   |  ??   | Family name |
| int32  |  0x1  | unknown |

list of sound names, each preceded by 4 bytes

| int32  |  0x1  | unknown |
| char   |       | Sequence name |
| char   |       | Sequence name |

**SOUND Structure**
|  Type  | Count | Description |
| :----- | ----: | :---------- |
| uint   |  0x1  | Sound name length (snl) |
| char   |  snl  | Sound name |
| short  |  0x1  | Start range |
| short  |  0x1  | End range |
| bool   |  0x1  | Flag |
| int32  |  0x1  | unknown  |

4 bytes??

| float  |  0x1  | unknown |
| float  |  0x1  | unknown |
| float  |  0x1  | unknown |
| float  |  0x1  | unknown |
| int32  |  0x1  | unknown |
| float  |  0x1  | Vector X |
| float  |  0x1  | Vector Y |
| float  |  0x1  | Vector Z |