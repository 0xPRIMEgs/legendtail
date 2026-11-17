# UV mapping that survives triangulation

## Treat UVs as a map of a surface

UV coordinates identify where each rendered triangle corner samples an image. They are not decorations attached to a polygon name. Two corners at the same geometric location can have different UVs across an intentional seam. Inside a triangle, interpolation determines where the image appears; a wrong corner can skew an entire panel.

Choose the mapping to match the surface and intended graphic. Planar projection is particularly useful for a flat armor panel with a straight center line. Seamed unwrapping is useful for curved organic surfaces. Cylindrical mapping can work for a tube, but needs an intentional seam and separate cap handling. Automatic methods are starting layouts that still require inspection.

## Use a shared projection for a shared graphic

For a panel with local horizontal coordinate h and vertical coordinate v, choose:

```text
u = u0 + scale_u * h
v_tex = v0 + scale_v * v
```

Apply that same function to every boundary and interior vertex in the panel. If a raised center is added, calculate its UV from its actual coordinates too. Assigning the four corners of a texture square to every trapezoid independently can change the graphic's direction across the diagonal. Giving an interior fan vertex a guessed texture center can pull the image away from its intended path.

An affine projection preserves straight graphic alignment in the chosen projection plane. It does not guarantee zero surface-area distortion on curved or strongly angled geometry. Inspect whether the chosen projection suits the actual shape. A multi-panel object can legitimately use several projections separated at designed seams.

## Diagnose with information-rich test textures

Use numbered cells, U/V arrows, asymmetrical letters, circles, and straight stripes. A plain checker detects some stretch but can hide a 90-degree rotation or a mirrored face. Render with the target filtering and check the final triangulation. Observe whether the problem follows a triangle diagonal, an island border, a mirrored side, or a material boundary.

| Symptom | Likely investigation |
|---|---|
| Line bends at an internal diagonal | Corner assignment or non-affine quad mapping |
| Fan of streaks from one point | Bad center UV or unsuitable polygon fan |
| Straight line becomes diagonal on a flat side | UV axes not aligned with actual surface axes |
| One face rotates the whole design | Corner order/UV orientation mismatch |
| Pattern matches nearby but jumps at a seam | Different scale, origin, or endpoint mapping |
| Correct in editor, wrong after export | Loop/corner UV loss, triangulation, V conversion, or material assignment |

## Map a boot as a constructed object

Separate ankle platform, sloping instep, toe, heel, sole, and side caps. The boot side is usually an irregular profile; mapping its vertices around a regular texture pentagon distorts the painted structure. Project the actual profile coordinates into its UV island.

For a light band that wraps around the boot, use the same height-to-V relation on sides, toe, and heel. Their U axes can differ because each face runs in a different horizontal direction. The band should meet at the same physical height, not merely at the same fraction of each face's own height. A toe face that begins halfway down the boot must sample the corresponding lower part of the shared vertical range.

Map sole tread across the width and along the sole's length deliberately. Do not inherit an arbitrary quad-corner order from the instep. See the exact [boot repair](../case-studies/uv-repairs.md).

## Preserve scale and margins

Allocate enough texels to the focal regions. A perfectly unwrapped face can still look muddy if its island is tiny. Add appropriate gutters and color dilation around islands; test minification and filtering rather than relying on a universal padding value. Keep packing from rotating directional patterns unless their artwork rotates with them.

## Repair narrowly and verify

For a UV-only repair, compare position arrays, topology, pivot data, textures, and other assets against the baseline. Then compare UV coordinates and the exported readback. Render the repaired area and the full figure. An affine residual can verify that a panel follows one projection, but it cannot prove that the chosen projection looks right. Visual and numeric checks answer different questions.

Further reading: [Blender UV operators](https://docs.blender.org/manual/en/4.2/modeling/meshes/editing/uv.html). Menu names and available methods vary by version.
