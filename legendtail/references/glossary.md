# Glossary

| Term | Meaning in Legendtail |
|---|---|
| Affine UV projection | A position-to-UV mapping using linear terms plus an offset; useful for coherent flat-panel graphics |
| Articulation | How connected body parts move relative to each other |
| Atlas | One image containing regions used by multiple surfaces or parts |
| Attachment frame | A position and orientation defining where and how a child part connects |
| Axis convention | The meaning and direction of coordinate axes in a specific space |
| Backface culling | Omitting triangles viewed from their designated back side |
| Baked transform | A transform applied into vertex or other stored data rather than retained as a separate operation |
| Bind pose | The reference configuration used to establish a skinned mesh's relation to its joints |
| Budget scope | Which instances, accessories, effects, and surfaces are included in a reported count |
| Checker texture | A diagnostic image used to reveal mapping scale and distortion; directional markings make it more informative |
| Closed shell | A surface intended to enclose volume without open borders |
| Connector index | The selected attachment slot on a parent part; distinct from a child name or rig-list index |
| Decimation | Algorithmic reduction of mesh complexity; requires visual and structural review |
| Degenerate triangle | A triangle with zero or negligibly small area under an appropriate scale-aware tolerance |
| Draw call | A rendering submission; its cost depends on the renderer and surrounding state |
| Emissive | A material contribution that appears self-lit; actual illumination and bloom are separate behaviors |
| Export readback | Loading and inspecting the written deliverable, rather than only its source scene |
| FK | Forward kinematics: composing a hierarchy's transforms to obtain assembled poses |
| GLB | The binary container form used by glTF |
| Gutter | Space around a UV island/tile that helps prevent neighboring image content from bleeding into samples |
| Hard edge | A deliberately discontinuous normal boundary used to preserve a sharp shading transition |
| Identity anchor | A feature or proportion important to recognizing the specific character |
| Inner frame | Structural material beneath or between outer armor parts; distinguish actual geometry from painted suggestion |
| Inverse bind matrix | A transform relating stored mesh coordinates to a joint's reference configuration for skinning |
| Island | A connected region of UV coordinates separated from others by seams |
| LOD | Level of detail: a separately chosen representation for a viewing/performance context |
| Local space | Coordinates relative to a specific object, part, or attachment rather than the entire world |
| MAMESH | A MechaAmazing mesh filename convention; the actual binary schema must be version-checked |
| MARG | Magic used by the inspected MechaAmazing pose/animation serialization; not interchangeable with GLB |
| Negative space | Empty space between or within forms that contributes to recognition |
| Normal | A direction used to describe a surface's orientation for shading and related operations |
| Overdraw | Repeated processing of overlapping surfaces/pixels, particularly relevant to layered effects |
| Pivot | The origin/frame about which a part's transformation is interpreted |
| Quaternion | A four-component rotation representation whose ordering and normalization conventions must be known |
| Rigid weighting | Giving a vertex one effective joint influence, preserving a part's shape during motion |
| Root motion | Movement of the character's root, distinct from internal limb articulation |
| Round trip | Exporting and re-importing data to compare preserved properties |
| Seam | A discontinuity in UV mapping; it may be intentional even when the geometry is continuous |
| Silhouette | The visible outer contour and relevant negative spaces of a shape |
| Texel | A pixel of a texture image |
| Texel density | Texture resolution allocated per amount of surface or visible area |
| Triangle soup | Geometry stored as independent triangle corner records rather than a shared indexed vertex mesh |
| Unlit | A material path whose displayed base appearance does not use ordinary scene lighting |
| UV | The two-dimensional coordinates used to sample a texture |
| Winding | The order of a triangle's vertices, which determines its oriented front/back convention |
| World space | Coordinates in the assembled scene rather than an individual part's local frame |

For symptoms and corrective actions, see [troubleshooting](../guides/20-troubleshooting.md).
