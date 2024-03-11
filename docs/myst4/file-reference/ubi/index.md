# `ubi` resource

## `ubi` resource file structure

| Name | Type | Description |
| :-- | --: | --- |
| magic | [`FileMagic`](../base.md#filemagic-string) | Magic signature. |
| ver | `uint32` | Global version. Individual resource types can have different binary contents depending on this version. |
| res | [`UbiResource`](#ubiresource-structure) | Resource. |

## `UbiResource` structure

| Name | Type | Description |
| :-- | --: | --- |
| type | [`UbiResourceType`](#ubiresourcetype-string) | Type. |
| data | ... | Data according to `type`. |

### `UbiResourceType` string

An `UbiResourceType` identifies the type of `ubi` resource that follows immediately after it.

This string value table might not be complete!

Type: [`BasicString`](../base.md#basicstring-structure)

| Value | Description |
| :-- | --- |
| [`"ares::ArrayVertexIndex"`](./ares-arrayvertexindex.md) |  |
| [`"ares::ArrayVertexPos"`](./ares-arrayvertexpos.md) |  |
| [`"ares::ArrayVertexNormal"`](./ares-arrayvertexnormal.md) |  |
| [`"ares::ArrayVertexColor"`](./ares-arrayvertexcolor.md) |  |
| [`"ares::ArrayVertexTexCoord"`](./ares-arrayvertextexcoord.md) |  |
| [`"ares::ArrayVertexBlendingIndex"`](./ares-arrayvertexblendingindex.md) |  |
| [`"ares::ArrayVertexBlendingWeight"`](./ares-arrayvertexblendingweight.md) |  |
| `"ares::UserArray"` | TODO |
| `"ares::SkinningParameters"` | TODO |
| `"ares::IndexedTriangleStrip"` | TODO |
| `"ares::IndexedTriangleList"` | TODO |
| `"ares::PointList"` | TODO |
| `"ares::LineList"` | TODO |
| `"ares::SpriteList"` | TODO |
| `"ares::SpriteList2D"` | TODO |
| `"ares::InterleavedPrimitive"` | TODO |
| `"ares::RenderTask"` | TODO |
| `"ares::Matrix"` | TODO |
| `"ares::RenderState"` | TODO |
| `"ares::Texture"` | TODO |
| `"ares::TextureFrame"` | TODO |
| `"ares::CameraOrthogonal"` | TODO |
| `"ares::CameraPerspective"` | TODO |
| `"ares::RenderMethod"` | TODO |
| `"ares::Effect"` | TODO |
| `"ares::Light"` | TODO |
| `"ares::ExternalDataContainer"` | TODO |
| `"ares_tools::Font"` | TODO |
| `"astra_renderer::ParticleSystemExternalData"` | TODO |
| `"astra_renderer::RendererNodeAres"` | TODO |
| `"atlas::CameraOrthogonal"` | TODO |
| `"atlas::CameraPerspective"` | TODO |
| `"atlas::GeometricInstance"` | TODO |
| `"atlas::GeometricInstanceLOD"` | TODO |
| `"atlas::Node"` | TODO |
| `"atlas::Light"` | TODO |
| `"MORE::Animation"` | TODO |
| `"MORE::Clip"` | TODO |
| `"MOREActor::ActorModel"` | TODO |
| `"MOREActor::SoundTable"` | TODO |
| `"snd::Familly"` | TODO |
| `"snd::InitValueConst < ubiU32 >"` | TODO |
| `"snd::InitValueRange < ubiU32 >"` | TODO |
| `"snd::InitValueSequence < ubiU32 >"` | TODO |
| `"snd::InitValueConst < ubiS32 >"` | TODO |
| `"snd::InitValueRange < ubiS32 >"` | TODO |
| `"snd::InitValueSequence < ubiS32 >"` | TODO |
| `"snd::InitValueConst < ubiF32 >"` | TODO |
| `"snd::InitValueRange < ubiF32 >"` | TODO |
| `"snd::InitValueSequence < ubiF32 >"` | TODO |
| `"snd::InitValueConst < ubi::Vector3 >"` | TODO |
| `"snd::InitValueRange < ubi::Vector3 >"` | TODO |
| `"snd::InitValueSequence < ubi::Vector3 >"` | TODO |
| `"snd::VirtualPanning"` | TODO |
| `"snd::Project"` | TODO |
| `"snd::FamillyPlaying"` | TODO |
| `"snd::FamillyPlayingSound"` | TODO |
| `"snd::Sequence"` | TODO |
| `"snd::Setting"` | TODO |
| `"snd::Sound"` | TODO |
| `"snd::SoundList"` | TODO |
