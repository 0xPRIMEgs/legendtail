# Case study: straightening torso graphics and repairing boots

## The torso symptom

The chest and back blue graphics veered toward the sides across tapered armor panels. The source construction used independently assigned UV corners and raised triangle-fan centers. A texture can be correct as an image while that mapping bends its motif on the mesh.

The repair used one position-derived projection for each relevant front/back panel, including the raised center vertices. With local coordinates x,y,z in the inspected mesh, the projection functions returned tile-local coordinates:

```text
chest front/back:
    u = 0.5 + y / 8.64
    v = (4.35 - z) / 5.15

abdomen front/back:
    u = 0.5 + y / 5.2
    v = (6.9 - z) / 7.65

upper pelvis front/back:
    u = 0.5 + x / 9.1
    v = (1.2 - y) / 4.7
```

These are asset-specific dimensions and axes. Do not paste them onto another torso. Recompute the origin and scale from that surface's intended graphic and extent. In this case, the functions apply only to the named panel regions; other surfaces retain their own mappings.

The recorded chest diagnostic residual fell from about 0.61237 to roughly 10⁻⁷ after the repair. This is the report's affine-fit diagnostic, not a general “UV quality score.” The useful conclusion is that the selected graphic panels now followed a consistent projection, and the actual renders were inspected to verify placement.

## The boot symptom

The boot sides stretched the light pattern diagonally, the toe carried a sideways stripe, and the sole inherited an unsuitable orientation. The side cap was an irregular five-point shape, but its UV fallback distributed vertices around a regular pentagon. The toe's generic quad mapping used the wrong surface direction.

## The actual profile

In the boot's local frame, X runs heel-to-toe, Y spans width, and Z runs downward. The side profile, in X/Z coordinates, is:

| Point | X | Z |
|---:|---:|---:|
| 0 | −1.72 | 0.35 |
| 1 | 0.80 | 0.35 |
| 2 | 3.68 | 2.48 |
| 3 | 3.42 | 4.43 |
| 4 | −1.72 | 4.43 |

The two sides lie at Y = −1.35 and +1.35. Five perimeter quads contribute ten triangles; two convex pentagonal caps contribute three each. Total: sixteen triangles per boot.

## The corrected projections

Both side caps use their actual X/Z coordinates:

```text
u_side = (x + 1.72) / 5.40
v_height = (z - 0.35) / 4.08
```

The toe and heel use the same `v_height`, with width mapped as `u_width = 0.5 + y/2.70`. This is the essential seam rule. The toe starts at Z = 2.48, so its top maps to about 0.522 of the full height range rather than resetting V to zero. As a result, the low light band meets the side at the same physical height.

The remaining surfaces use explicit length/width maps:

```text
ankle platform: u = u_width, v = (x + 1.72) / 2.52
sloping instep: u = u_width, v = (x - 0.80) / 2.88
sole tread:    u = u_width, v = (x + 1.72) / 5.14
toe and heel:  u = u_width, v = v_height
```

The heel changed to the same boot-pattern tile used for the wrapping band. No texture pixels changed. The side maps are planar in the profile coordinates, while the perimeter surfaces have their own semantic orientation.

## Tile placement

The inspected atlas has 4×4 tiles of 128 pixels in a 512×512 image. The authoring helper places a tile-local coordinate s,t with:

```text
atlas_u = (tile_x + 3 + 122*s) / 512
atlas_v = (tile_y + 3 + 122*t) / 512
```

Those constants describe this atlas helper, not a universal gutter recommendation. Image-origin conversion to the preview's UV convention is handled at the export boundary. Apply such a conversion once and test it; blindly flipping V in multiple stages can cancel or reintroduce an error.

## Evidence from the repair

- Only `foot.mamesh` changed relative to the prior torso-corrected asset set and game backup.
- Forty-four of its forty-eight triangle-list vertex UV records changed.
- Positions, vertex order, pivot header, textures, other parts, and animations remained identical.
- Each boot remained sixteen triangles; the assembled character remained 400.
- Side-panel affine-fit residuals were about 2.04×10⁻⁸ in stored UV coordinates.
- Shared side/toe/heel height mapping differed from the intended relation by at most about 2.92×10⁻⁸ after float storage.
- Toe, side, underside, oblique, and full-model views were inspected; the 120-frame orbit was regenerated.

The transferable fix is **surface-aware mapping with shared physical coordinates where graphics cross seams**. The exact profile and scale values belong to this boot. Applying a mathematically consistent map to the wrong surface region would still be a mistake.
