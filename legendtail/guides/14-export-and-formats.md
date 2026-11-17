# Export formats and readback

## The delivered file is the product

Keep an editable source, but validate the format the game will load. Export can change triangulation, vertex splits, materials, hierarchy, or animation sampling. Re-open the result through an independent read path where practical. A source scene that looks correct cannot establish that every exported field is correct.

Define units, axes, root transform, material behavior, image embedding, animation names, and supported features in the asset contract. Preserve relative texture paths when images are external. Verify all referenced files are present in the package.

## GLB checks

For glTF triangle primitives, count index elements divided by three, or position elements divided by three for non-indexed triangles. Inspect primitive mode first; strip and fan modes need their own interpretation. Report unique mesh triangles separately from scene instances if a mesh is used more than once. Validate buffer ranges and accessor/component types before trusting counts.

For a rigid skinned export, inspect joint references and weights on every vertex. Ensure the joint indices address the skin's joint list and that bind transforms reproduce the intended rest assembly. See the [glTF specification](https://registry.khronos.org/glTF/specs/2.0/glTF-2.0.html) for format requirements; see the [Khronos skinning tutorial](https://github.khronos.org/glTF-Tutorials/gltfTutorial/gltfTutorial_020_Skins.html) for the transform relationship.

Distinguish an unlit material from an emissive PBR material. Choose what the target viewer supports and verify the exported declaration. Do not assume that a desktop editor's node graph will be reproduced by a small custom loader. Export only the character and intended attachments; exclude the turntable stage, camera, and lights from the asset file unless requested.

## Observed BU24 MAMESH layout

The inspected replacement files use this specific binary layout. This table documents those files; it is not a universal .mamesh specification. Inspect the current MAIO implementation for any other version.

| Byte offset | Field | Observed encoding |
|---:|---|---|
| 0 | Magic | Big-endian uint32, 0x4D415032, ASCII MAP2 |
| 4 | Version | Big-endian uint32, value 1 |
| 8 | Base orientation | Four big-endian float32 values, xyzw quaternion |
| 24 | Child count c | Big-endian 32-bit count |
| 28 | Child records | c records, each xyz position plus xyzw quaternion; 28 bytes each |
| 28 + 28c | Vertex count n | Big-endian 32-bit count |
| 32 + 28c | Vertex records | n records of x,y,z,u,v; five float32 values, 20 bytes each |

The geometry is a triangle list: three successive vertex records form one triangle. The observed files have no separate index buffer and no per-vertex RGBA field in this layout. Older descriptions with other fields must not be mixed into this serializer. The expected file length is `32 + 28*c + 20*n` bytes for this version.

Validate magic/version, bounds on counts, exact length, finite values, and `n % 3 == 0`. Reject or explicitly handle unsupported versions. Do not infer correctness just because a file extension matches. For a pivot-preserving replacement, compare the relevant header bytes before and after.

## Animation and schema boundaries

The inspected animation path uses named pose channels and a separate MARG format. Do not assume that a GLB animation can be renamed to become a .marig animation. Read the real serializer, represent its timing and transform conventions correctly, and compare playback with a known-good clip.

Likewise, do not rename a ZIP, JAR, or desktop executable to an ISO or ROM and describe it as a platform port. A port requires the target runtime and packaging toolchain. Asset export, engine integration, and platform build are distinct deliverables.

## Package readback

Extract the final archive into a clean directory. Confirm the intended entry paths and image references resolve there, with case-sensitive names where relevant. Load the delivered mesh, not a leftover authoring copy. Verify that included previews and reports correspond to that revision. Preserve a source/loader version note so a later change can be diagnosed without guessing.
