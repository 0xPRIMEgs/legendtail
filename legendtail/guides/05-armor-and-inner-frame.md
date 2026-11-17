# Armor, inner frames, and luminous recesses

## Decide what “under the armor” means

A blue stripe painted on top of a plate, a painted recess, and an actual opening with an inner surface are different constructions. Choose intentionally. If the brief requires a visible inner frame, do not describe a flat texture as physical depth. If the budget leads to a painted approximation, say so and verify that the approximation is acceptable at the required camera.

| Construction | What it provides | What it cannot provide |
|---|---|---|
| Surface stripe | Color identification at minimal geometry cost | Recess silhouette or parallax |
| Painted recess | Dark border, highlight lip, and apparent depth from a chosen surface | Real occlusion across changing views |
| Real window and inner panel | Visible separation, cavity sides, view-dependent depth | Free geometry or zero overdraw |
| Separate exposed frame segment | Articulation and a distinct structural layer | Automatic clearance from surrounding armor |

## Reserve physical depth where it matters

Prioritize large chest windows, visible shoulder gaps, major helmet openings, or places where the camera sees the cavity edge. Small vents and fasteners can usually be painted at severe budgets. A few convincing depth cues can establish the material language for many simpler surfaces.

For a real window, construct the outer border, cavity side walls where visible, and the inner panel at a lower depth. Avoid coplanar overlap; it produces unstable depth ordering. Check from oblique angles and through animation. Do not let the inner panel protrude beyond the outer armor when the part rotates.

If multiple rigid parts expose a shared-looking frame, decide whether the frame belongs to one joint, is segmented across joints, or is a separate rig element. A continuous texture pattern does not establish a mechanically valid connection.

## Make the light readable without relying on bloom

Use a dark structural border and a sufficiently broad light region. Keep the brightest center smaller than the whole panel so its shape remains legible. At game resolution, very narrow lines can disappear or flicker. Choose width by downsampled inspection, not only by the high-resolution atlas.

The BlissFire3 texture design used broad luminous regions roughly 28–44% of selected limb-panel widths. That is a measured design choice from one robot, not a universal ratio. A smaller character or a different material style may require another width.

Painted bright color, an unlit material, an emissive material, bloom, and actual scene illumination are separate features. State which one the engine supports. A cyan texel can look luminous through contrast without emitting light. Do not rely on a renderer-only glow to sell a runtime asset.

## Protect the mechanical hierarchy

Keep broad armor masses distinct from dark joints and the inner frame. Avoid making every seam equally bright; too many competing lines fragment the figure. Use the light pattern to reinforce the body structure and focal hierarchy. A central chest motif should stay centered through the torso's taper, which requires coherent UVs rather than independent per-triangle guesses.

## Inspect all exposed surfaces

Review front, back, sides, underarms, groin, soles, and the underside of raised limbs. Hidden structural surfaces should have intentional materials. An unfinished underside can appear during a single jump frame and break the illusion more than an absent tiny bevel.

For a 400-triangle asset, record every real cavity's cost. If the result exceeds the cap, simplify a less important silhouette region or reduce the cavity construction deliberately. Do not remove required depth silently and keep describing the model as physically layered.
