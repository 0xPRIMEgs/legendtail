# Validation: appearance, structure, and runtime

## Keep three conclusions separate

An asset can be attractive but invalid, structurally valid but unattractive, or correct in a renderer but incompatible with the game. Report visual review, data checks, and runtime checks independently. A single “passed” flag conceals too much.

| Layer | What to inspect | What it does not prove |
|---|---|---|
| Visual | Silhouette, proportions, UVs, materials, motion | Correct file layout or target performance |
| Structural | Counts, indices, winding, finite data, bindings, references | Appealing design or expressive animation |
| Runtime | Actual loader, draw path, animation, collision implications, performance | Behavior on an untested platform |

## Validate the budget at the boundary

Count exported triangles by primitive mode and assembled instances. Include the agreed accessories and duplicated sides. Record texture dimensions and relevant material/draw counts. Distinguish an exact cap from an approximate target. Keep the source count for comparison, but make the output count authoritative.

For geometry, check degenerate triangles and consistent winding. For intended closed shells, check edge incidence. Also inspect self-intersections, internal faces, and intentional openings; topology checks alone are not enough. Review mirrored parts with culling enabled.

## Validate UVs according to their intent

Check finite coordinates, expected atlas ranges, seam continuity, orientation, and filtering. Coordinates outside 0–1 may be legitimate for repeating textures; do not reject them universally. For a non-repeating atlas, confirm islands remain within their allowed regions and gutters.

For a planar graphic panel, fit an affine map from projected positions to UVs and inspect the residual. A large residual can expose inconsistent corner or center assignment. A low residual only proves consistency with that model; it does not prove the graphic is centered, upright, or aesthetically suitable.

For a wrapping band, compare the shared physical coordinate-to-texture relation at seams. This is stronger than checking only whether UV endpoints have identical values, since different islands can use different U ranges while meeting at the correct height.

## Validate a compatible rig replacement

Compare names, hierarchy, connector order, pivot frames, and local coordinate semantics. When the interface is stored as a preserved binary header, byte equality is a useful direct check. Then load the replacement with the actual engine library and sample representative existing animations.

Measure joint positions or transformed vertices using a reference implementation. State the tolerance and units. For a CPU/Blender comparison, align coordinate spaces first. A small difference after basis conversion is informative; a small difference after an undocumented compensating transform can hide the real error.

Preserved joint positions do not prove preserved collision behavior if hitboxes or bounds are derived from mesh dimensions. Test those dependencies when the geometry changes. A UV-only change should leave geometry-derived bounds identical.

## Validate animations beyond file presence

Check clip names, joint coverage, key times, interpolation, loop length, and root-motion policy. Inspect extremes and transitions. Confirm a hit/release event is connected if gameplay integration is claimed. A file containing 120 keyframes can still contain a frozen pose or unintended synchronized motion among instances.

## Use a focused regression comparison

For a UV-only repair, compare positions, triangle ordering, pivot data, textures, other mesh files, and animation bytes with the baseline. For a texture-only correction, compare geometry and UVs. For a geometry change, preserve the rig interface and reassess bounds and motion clearance. Tests should protect the real contract, not just repeat implementation details.

## Report limits precisely

Say “loaded by the BU24 library and sampled across 23 clips” when that is what happened. Do not expand it into “works on all MA versions and consoles.” State which renders were visually inspected and which runtime/hardware paths remain untested. Reuse valid prior evidence only when the current change leaves its premises unchanged, and explain that relationship.

Use [the review template](../templates/review-report.md) and [the measured case study](../case-studies/blissfire3-400.md).
