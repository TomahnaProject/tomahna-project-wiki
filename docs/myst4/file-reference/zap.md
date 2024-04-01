# ZAP

A container of multiple image files. These are used for transparency layers in static textures. One major example is nodecube textures, where transparency lets the skybox through.

It is unknown what "ZAP" is supposed to stand for, if anything.

ZAP files are little-endian, and have the .zap file extension.

## `ZAP` file structure

| Name | Type | Description |
| :-- | :-- | --- |
| hdrSize | `uint32` | Header size. Never observed to be anything other than `0x20`. |
| nImages | `uint32` | Number of images. Never observed to be anything other than `0x2`. Then again, Revelation is _hardcoded_ to assume all ZAP files contain exactly two images. |
| formats | `uint32`\[`nImages`\] | Formats of the respective images, as known by the [LEADTOOLS SDK](https://www.leadtools.com/help/sdk/main/api), though only three are supported (`FILE_JPEG` (`0xA`), `FILE_TIF_JPEG` (`0xB`) and `FILE_PNG` (`0x4B`)). |
| sizes | `uint32`\[`nImages`\] | Sizes of the respective image's data. |
| w | `uint32` | Shared width. |
| h | `uint32` | Shared height. |
| data | `uint8`\[`sizes`\[`i`\]\]\[`nImages`\] | Data of the respective image. |
