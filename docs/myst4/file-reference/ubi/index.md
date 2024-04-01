# `ubi` resource

## `ubi` resource file structure

| Name | Type | Description |
| :-- | :-- | --- |
| magic | [`FileMagic`](../base.md#filemagic-string) | Magic signature. |
| ver | `uint32` | Global version. Individual resource types can have different binary contents depending on this version. |
| res | [`UbiResource`](#ubiresource-structure) | Resource. |

## `UbiResource` structure

| Name | Type | Description |
| :-- | :-- | --- |
| type | [`UbiResourceType`](#ubiresourcetype-string) | Type. |
| data | ... | Data according to `type`. |

### `UbiResourceType` string

- Type: [`BasicString`](../base.md#basicstring-structure)

An `UbiResourceType` identifies the type of `ubi` resource that follows immediately after it.

This string value table might not be complete!

| Value |
| :-- |
| [`"ares::ArrayVertexIndex"`](./ares-arrayvertexindex.md) |
| [`"ares::ArrayVertexPos"`](./ares-arrayvertexpos.md) |
| [`"ares::ArrayVertexNormal"`](./ares-arrayvertexnormal.md) |
| [`"ares::ArrayVertexColor"`](./ares-arrayvertexcolor.md) |
| [`"ares::ArrayVertexTexCoord"`](./ares-arrayvertextexcoord.md) |
| [`"ares::ArrayVertexBlendingIndex"`](./ares-arrayvertexblendingindex.md) |
| [`"ares::ArrayVertexBlendingWeight"`](./ares-arrayvertexblendingweight.md) |
| `"ares::UserArray"` |
| `"ares::SkinningParameters"` |
| `"ares::IndexedTriangleStrip"` |
| `"ares::IndexedTriangleList"` |
| `"ares::PointList"` |
| `"ares::LineList"` |
| `"ares::SpriteList"` |
| `"ares::SpriteList2D"` |
| `"ares::InterleavedPrimitive"` |
| `"ares::RenderTask"` |
| [`"ares::Matrix"`](./ares-matrix.md) |
| [`"ares::RenderState"`](./ares-renderstate.md) |
| [`"ares::Texture"`](./ares-texture.md) |
| [`"ares::TextureFrame"`](./ares-texture.md) |
| [`"ares::CameraOrthogonal"`](./ares-camera.md#arescameraorthogonal) |
| [`"ares::CameraPerspective"`](./ares-camera.md#arescameraperspective) |
| `"ares::RenderMethod"` |
| `"ares::Effect"` |
| `"ares::Light"` |
| `"ares::ExternalDataContainer"` |
| [`"ares_tools::Font"`](./arestools-font.md) |
| `"astra_renderer::ParticleSystemExternalData"` |
| `"astra_renderer::RendererNodeAres"` |
| `"atlas::CameraOrthogonal"` |
| `"atlas::CameraPerspective"` |
| `"atlas::GeometricInstance"` |
| `"atlas::GeometricInstanceLOD"` |
| `"atlas::Node"` |
| `"atlas::Light"` |
| [`"MORE::Animation"`](./more-animation.md) |
| `"MORE::Clip"` |
| `"MOREActor::ActorModel"` |
| `"MOREActor::SoundTable"` |
| `"snd::Familly"` |
| `"snd::InitValueConst < ubiU32 >"` |
| `"snd::InitValueRange < ubiU32 >"` |
| `"snd::InitValueSequence < ubiU32 >"` |
| `"snd::InitValueConst < ubiS32 >"` |
| `"snd::InitValueRange < ubiS32 >"` |
| `"snd::InitValueSequence < ubiS32 >"` |
| `"snd::InitValueConst < ubiF32 >"` |
| `"snd::InitValueRange < ubiF32 >"` |
| `"snd::InitValueSequence < ubiF32 >"` |
| `"snd::InitValueConst < ubi::Vector3 >"` |
| `"snd::InitValueRange < ubi::Vector3 >"` |
| `"snd::InitValueSequence < ubi::Vector3 >"` |
| `"snd::VirtualPanning"` |
| `"snd::Project"` |
| `"snd::FamillyPlaying"` |
| `"snd::FamillyPlayingSound"` |
| `"snd::Sequence"` |
| `"snd::Setting"` |
| `"snd::Sound"` |
| `"snd::SoundList"` |

## `UbiSubResource` structure

A `UbiSubResource` can be either a reference to an external [`ubi` resource file](#ubi-resource-file-structure), or contain an embedded [`UbiResource`](#ubiresource-structure).

| Name | Type | Condition | Description |
| :-- | :-- | :-- | --- |
| valid | `bool` |  |  |
| path | [`BasicString`](../base.md#basicstring-structure) | `valid` | Virtual path to [`ubi` resource file](#ubi-resource-file-structure). |
| data | [`UbiResource`](#ubiresource-structure) | `valid && path.len == 0` | Embedded resource. |
