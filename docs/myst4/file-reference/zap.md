# Zap

A container of multiple image files. These are used for transparency layers in static textures. One major example is nodecube textures, where transparency lets the skybox through.

It is unknown what "zap" is supposed to stand for, if anything.

Zap files are little-endian, and have the .zap file extension.

## `ZAP` structure

| Name | Type | Description |
| :-- | --: | --- |
| headerSize | `uint32` | Header size. Never observed to be anything other than `0x20`. |
| numImages | `uint32` | Number of images. Never observed to be anything other than `0x2`. Then again, Revelation is _hardcoded_ to assume all zap files contain exactly two images. |
| formats | `uint32[numImages]` | Formats of the respective images, as known by the [LEADTOOLS SDK](https://www.leadtools.com/help/sdk/main/api), though only three are supported (`FILE_JPEG` (`0xA`), `FILE_TIF_JPEG` (`0xB`) and `FILE_PNG` (`0x4B`)). Never observed to be anything other than `FILE_JPEG`. |
| sizes | `uint32[numImages]` | Sizes of the respective image's data. |
| width | `uint32` | Shared width. |
| height | `uint32` | Shared height. |
| data | `uint8[sizes[i]][numImages]` | Data of the respective image. |
