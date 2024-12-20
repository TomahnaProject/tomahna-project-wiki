# `thor` resource

`thor` is the namespace that houses Revelation's engine implementation. It has its own dedicated resource serialisation scheme.

## `thor` resource file structure

| Name | Type | Description |
| :-- | :-- | --- |
| magic | [`FileMagic`](../base.md#filemagic-string) | Magic signature. |
| resource | [`ThorResource`](#thorresource-structure) | Resource. |

## `ThorResource` structure

| Name | Type | Description |
| :-- | :-- | --- |
| type | [`ThorResourceType`](#thorresourcetype-enum) |  |
| data | ... | Data according to `type`. |

### `ThorResourceType` enum

- Type: `uint32`

A `ThorResourceType` identifies the type of `thor` resource that follows immediately after it.

This enum value table might not be complete!

| Name | Value | Omits [header](#thorresourceheader-structure) |
| :-- | :-- | --- |
| `AiResource` | `0x01` |  |
| `AtlasNodeResource` | `0x02` |  |
| `BlenderResource` | `0x03` |  |
| [`CommandBlock`](./commandblock.md) | `0x06` |  |
| [`ContainerResource`](./containerresource.md) | `0x07` |  |
| `Context` | `0x08` | * |
| `CursorResource` | `0x09` |  |
| `FlareResource` | `0x0A` |  |
| `FontResource` | `0x0B` |  |
| [`GeometryResource`](./geometryresource.md) | `0x0C` |  |
| `HotspotResource` | `0x0D` |  |
| `Interpolator` | `0x0E` |  |
| [`TextureBox`](./texturebox.md) | `0x0F` |  |
| `LayerExtractResource` | `0x10` |  |
| `LightResource` | `0x11` |  |
| `LightmapModAddResource` | `0x13` |  |
| `LightsetResource` | `0x14` |  |
| `MaterialResource` | `0x15` |  |
| `MoreActor` | `0x16` |  |
| `MoreClip` | `0x17` |  |
| `MoreModel` | `0x18` |  |
| `MoreMultiActor` | `0x19` |  |
| `GraphicOverlay` | `0x1A` |  |
| `PanelResource` | `0x1B` |  |
| `AnimPanelResource` | `0x1C` |  |
| [`ParticleSystemBase`](./particlesystembase.md) | `0x1D` |  |
| `PixelEffectResource` | `0x1E` |  |
| [`RailResource`](./railresource.md) | `0x1F` |  |
| `SkyReflectionResource` | `0x21` |  |
| `SoundLoader` | `0x23` |  |
| [`Subtitle`](./subtitle.md) | `0x24` |  |
| [`TextResource`](./textresource.md) | `0x25` |  |
| [`Text`](./text.md) | `0x26` | * |
| [`TextureResource`](./textureresource.md) | `0x27` |  |
| [`VariableResource`](./variableresource.md) | `0x28` |  |
| [`Video`](./video.md) | `0x29` |  |
| `WaterResource` | `0x2A` |  |
| `InteractiveOffsetProvider` | `0x2B` |  |
| `TextureAlignedOffsetProvider` | `0x2C` |  |
| `StateData` | `0x2D` |  |
| `WidgetResource` | `0x2E` |  |
| `Widget2D` | `0x2F` |  |
| `Button` | `0x30` |  |
| `Canvas` | `0x31` |  |
| `ComboBox` | `0x32` |  |
| `Label` | `0x33` |  |
| `ListBox` | `0x34` |  |
| `ListBoxItem` | `0x35` |  |
| `PanelWidget` | `0x36` |  |
| `PanelButton` | `0x37` |  |
| `Popup` | `0x38` |  |
| `Credits` | `0x39` |  |
| `TextWidget` | `0x3A` |  |
| `ToolTips` | `0x3B` |  |
| `ZipWidget` | `0x3C` |  |
| `Slider` | `0x3D` |  |
| `ZPlanesResource` | `0x3E` |  |
| `MultiGeometry` | `0x40` |  |
| `QualityDatabaseResource` | `0x41` |  |
| `ShadowMaterialResource` | `0x42` |  |

### `ThorResourceHeader` structure

A `ThorResourceHeader` contains the base info for a `thor` resource.

| Name | Type | Description |
| :-- | :-- | --- |
| version | `uint32` | Indicates which revision of a particular resource type this resource was compiled as. Though there are resource types with multiple versions, Revelation's code appears to ignore this field, always assuming the latest version; some resource headers do _not_ list the latest version. Unlike [`ubi` resource](../ubi/index.md) file versions, this version field pertains to just the associated individual resource. |
| name | [`EncryptedString`](../base.md#encryptedstring-structure) | For non-embedded resources, this must be the filename without extension. |
