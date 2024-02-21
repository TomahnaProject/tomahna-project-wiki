# `thor` resource

`thor` is the namespace that houses Revelation's engine implementation. It has its own dedicated resource serialisation scheme.

## `thor` resource file structure

| Name | Type | Description |
| :-- | --: | --- |
| magic | [`FileMagic`](../base.md#filemagic-string) | Magic signature. |
| res | [`ThorResource`](#thorresource-structure) | Resource. |

## `ThorResource` structure

| Name | Type | Description |
| :-- | --: | --- |
| type | [`ThorResourceType`](#thorresourcetype-enum) | Type. |
| data | ... | Data according to `type`. |

### `ThorResourceType` enum

A `ThorResourceType` identifies the type of `thor` resource that follows immediately after it.

This enum value table might not be complete!

Type: `uint32`

| Name | Value | Description |
| :-- | --: | --- |
| `AiResource` | `0x1` | TODO |
| `AtlasNodeResource` | `0x2` | TODO |
| `BlenderResource` | `0x3` | TODO |
| `CommandBlock` | `0x6` | TODO |
| `ContainerResource` | `0x7` | TODO |
| `Context` | `0x8` | TODO |
| `CursorResource` | `0x9` | TODO |
| `FlareResource` | `0xA` | TODO |
| `FontResource` | `0xB` | TODO |
| `GeometryResource` | `0xC` | TODO |
| `HotspotResource` | `0xD` | TODO |
| `Interpolator` | `0xE` | TODO |
| `TextureBox` | `0xF` | TODO |
| `LayerExtractResource` | `0x10` | TODO |
| `LightResource` | `0x11` | TODO |
| `LightmapModAddResource` | `0x13` | TODO |
| `LightsetResource` | `0x14` | TODO |
| `MaterialResource` | `0x15` | TODO |
| `MoreActor` | `0x16` | TODO |
| `MoreClip` | `0x17` | TODO |
| `MoreModel` | `0x18` | TODO |
| `MoreMultiActor` | `0x19` | TODO |
| `GraphicOverlay` | `0x1A` | TODO |
| `PanelResource` | `0x1B` | TODO |
| `AnimPanelResource` | `0x1C` | TODO |
| `ParticleSystemBase` | `0x1D` | TODO |
| `PixelEffectResource` | `0x1E` | TODO |
| `RailResource` | `0x1F` | TODO |
| `SkyReflectionResource` | `0x21` | TODO |
| `SoundLoader` | `0x23` | TODO |
| `Subtitle` | `0x24` | TODO |
| `TextResource` | `0x25` | TODO |
| `Text` | `0x26` | TODO |
| [`TextureResource`](./textureresource.md) | `0x27` |  |
| `VariableResource` | `0x28` | TODO |
| `Video` | `0x29` | TODO |
| `WaterResource` | `0x2A` | TODO |
| `InteractiveOffsetProvider` | `0x2B` | TODO |
| `TextureAlignedOffsetProvider` | `0x2C` | TODO |
| `StateData` | `0x2D` | TODO |
| `WidgetResource` | `0x2E` | TODO |
| `Widget2D` | `0x2F` | TODO |
| `Button` | `0x30` | TODO |
| `Canvas` | `0x31` | TODO |
| `ComboBox` | `0x32` | TODO |
| `Label` | `0x33` | TODO |
| `ListBox` | `0x34` | TODO |
| `ListBoxItem` | `0x35` | TODO |
| `PanelWidget` | `0x36` | TODO |
| `PanelButton` | `0x37` | TODO |
| `Popup` | `0x38` | TODO |
| `Credits` | `0x39` | TODO |
| `TextWidget` | `0x3A` | TODO |
| `ToolTips` | `0x3B` | TODO |
| `ZipWidget` | `0x3C` | TODO |
| `Slider` | `0x3D` | TODO |
| `ZPlanesResource` | `0x3E` | TODO |
| `MultiGeometry` | `0x40` | TODO |
| `QualityDatabaseResource` | `0x41` | TODO |
| `ShadowMaterialResource` | `0x42` | TODO |

### `ThorResourceHeader` structure

A `ThorResourceHeader` contains the base info for a `thor` resource.

!!! note inline end

    Not every resource type includes this header!

| Name | Type | Description |
| :-- | --: | --- |
| ver | `uint32` | Version, indicating which revision of a particular resource type this resource was compiled as. Though there are resource types with multiple versions, none are known to check for the version, always assuming the latest version. Unlike [`ubi` resource](../ubi-resource.md) file versions, this version field pertains to just the associated individual resource. |
| name | [`EncryptedString`](../base.md#encryptedstring-structure) | Name. For non-embedded resources, this will be the filename without extension. |
