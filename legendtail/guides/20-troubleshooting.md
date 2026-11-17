# Troubleshooting by symptom

Begin with the actual exported asset and a known baseline. Locate the layer responsible before changing it: reference/design, geometry, UVs, texture, rig, export, renderer, gameplay, or packaging.

| Symptom | First check | Typical correction | Proof |
|---|---|---|---|
| Character is recognizable only from the front | Side silhouette and depth landmarks | Reshape the major volumes | Matched front/side/three-quarter clay renders |
| Chest/back line bends toward the edges | Per-face UV assignment and fan center | Use a coherent panel projection | Straight-line test and actual atlas render |
| Boot side looks diagonally stretched | Side cap mapped as a regular polygon | Project actual boot profile | Side close-up plus affine mapping check |
| Toe stripe is vertical | UV corner order and surface axes | Map across boot width and shared height | Toe and oblique views |
| Band jumps at toe/side seam | Each face normalizes its own height | Use one physical height-to-V relation | Seam samples and close-up |
| Sole tread runs the wrong direction | Generic quad UV orientation | Give the sole an explicit length/width mapping | Underside view |
| Texture leaks neighboring tile color | Gutters, filtering, mip levels | Dilate edges and revise padding/layout | Target-size filtered render |
| Face disappears or blends into background | Alpha and background-colored paint | Repair face art/geometry/material | Several backgrounds and side view |
| Tail has repeated bright rings | Tile restarted on every segment | Use continuous longitudinal mapping | Full tail in profile and orbit |
| Thin appendage vanishes | Thickness, culling, screen size | Reshape or deliberately use a supported card | Both sides at game resolution |
| Right leg/arm bends incorrectly | Mirror of connectors and orientation | Mirror complete frames once | Asymmetric pose in native runtime |
| Rest pose works, animation explodes | Bind/local frames and transform order | Correct space conversion and hierarchy | Native/export vertex comparison |
| Part rotates about its center incorrectly | Pivot origin and baked transforms | Restore the intended pivot interface | Known-angle marker test |
| Faces vanish from outside | Winding after reflection/export | Correct winding and normals | Culling-enabled orbit |
| New mesh changes combat reach | Bounds-derived collision attachments | Review geometry dependencies or explicit shapes | In-game collision visualization |
| Every fighter animates together | Shared mutable animation state | Separate instance state or apply it per draw | Two fighters in different motions |
| Effects detach or rotate oddly | Attachment/spawn space | Apply the correct frame once | Frame-by-frame attack review |
| Fireball spawns only once | Gameplay state/event handling | Diagnose code rather than remaking geometry | Repeated attack runtime test |
| Loader says a mesh needs review | Magic/version/layout/length | Match the current serializer | Native loader succeeds on exact output |
| GLB looks different from source | Material/UV/transform export | Inspect and correct exported representation | Independent readback |
| Console preview looks worse | Actual asset, filter, material, resolution | Isolate the mismatch | Matched labeled runtime captures |
| Turntable is old despite new assets | Stale frames or wrong scene file | Render into a clean/current-run directory | Completed render log and sampled output |
| ZIP downloads but model is incomplete | Internal paths and missing textures | Rebuild a self-contained package | Clean extraction and load |

## A focused repair loop

1. Reproduce the symptom in a stable view or runtime action.
2. Identify the smallest responsible representation.
3. Preserve a baseline and state the intended edit.
4. Apply the repair to the canonical source.
5. Re-export and inspect the affected region plus its dependencies.
6. Compare fields that should remain unchanged.
7. Deliver the corrected revision with its evidence.

## Avoid misleading quick fixes

Do not disable culling to hide reversed faces, add bloom to hide a narrow or broken light pattern, repaint the background over a hole, or rotate the camera away from a bad profile. Do not add triangles before determining whether the defect is actually UV mapping. Conversely, do not force a texture fix when the required silhouette or articulation needs geometry.

If a proposed repair changes a stable interface, explain the compatibility cost and verify the consumers. The best repair removes the cause while preserving the user's accumulated approved work.
