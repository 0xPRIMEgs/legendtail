# Runtime cost and retro targets

## A low triangle count is only one cost

Rendering cost also depends on draw calls, materials, texture transfers, skinning or CPU transforms, animation updates, visibility, overdraw, resolution, and the rest of the game. Four hundred triangles drawn as many poorly managed objects can behave differently from a compact batched asset. Profile the actual implementation rather than predicting performance from the mesh count alone.

Track the number of visible actors and effects. A harmless transparent aura in isolation can be expensive when several overlap. A large texture atlas can reduce material switches but still consume memory or require conversion on a constrained backend. An unlit style may simplify shading without reducing animation or submission cost.

## Match the actual render path

Identify whether the engine uses CPU-transformed vertices, GPU buffers, rigid part transforms, skinning, or a fallback. Verify texture binding, UV submission, culling, and matrix application in that path. A model that works through one path can reveal stale buffers or unsupported attributes through another.

If the game shares an avatar resource among fighters, keep per-instance state distinct. Apply each fighter's pose and texture as required by the implementation and verify that cached transforms are updated correctly. Do not assume that a method named “prepare” or “draw” performs a particular GPU operation without reading it.

## Compare renders without guessing the cause

If a PSP or another target looks worse than a desktop preview, capture matching pose, camera, resolution, texture, and lighting settings where possible. Check texture resampling, palette/format conversion, filtering, UV precision, culling, material support, aspect ratio, and gamma/color handling. Change one suspected factor at a time.

Do not blame the hardware merely because the image differs. A conversion can have supplied a different LOD, texture, or coordinate convention. Conversely, do not claim desktop equivalence when the target intentionally uses a simpler material or lower-resolution image.

## Establish a platform matrix

| Target | Required evidence before claiming support |
|---|---|
| Desktop development renderer | Export load, material display, animation, representative performance capture |
| Actual game runtime | Same asset through the game loader, camera, animation, and collision dependencies |
| PSP build | Target loader/material compatibility and a labeled runtime test on emulator or hardware |
| Dreamcast build | Target format/toolchain integration and a labeled runtime test |
| N64 build | Target format/toolchain integration and a labeled runtime test |
| Android build | Actual graphics backend, packaging, and device/runtime behavior when claimed |

This table is a validation plan, not a list of platforms certified by Legendtail. Hardware and emulator evidence are distinct. Record the exact build and environment used.

## Choose optimizations from measurements

Measure a representative scene with the expected actors and effects. Identify whether the bottleneck is CPU animation, draw submission, fill, texture bandwidth, or another system. Then target that cost. Reducing a model from 3k to 400 triangles may help a geometry-bound case but cannot fix excessive state changes or an unrelated gameplay loop.

Avoid universal texture-size or triangle-limit claims for a console. The available budget depends on the engine, scene, material path, and performance target. Use the smallest representation that meets the visual brief and measured constraints, while keeping a higher-quality source where useful.

## Keep packaging honest

An asset package is not a console port. A desktop render is not a hardware capture. A ROM/ISO/APK needs the appropriate executable, assets, packaging, and validation. Label each deliverable by what it actually contains and retain the platform-specific source/build notes when requested.
