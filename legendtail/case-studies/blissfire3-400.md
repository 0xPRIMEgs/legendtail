# Case study: the BlissFire3 400-triangle robot

## What was inspected

This example comes from the corrected `BlissFire3_Robot_400.zip` package associated with the BlissFire3 BU24 workflow. Its source, reports, and final asset data were inspected when preparing this handbook. The case is a measured construction and compatibility example, not proof that 400 triangles is sufficient for every requested style or a benchmark against a human artist.

The source robot contained 3,804 triangles. The replacement contains exactly 400 in the assembled humanoid, including mirrored right limbs. It uses eleven authored mesh files to fill seventeen rigid slots. Small armor detail is painted into six aligned 512×512 atlas variants: the base plus five player color variants.

## Exact budget

| Authored part | Triangles per instance | Instances | Assembled triangles |
|---|---:|---:|---:|
| groin | 28 | 1 | 28 |
| abs | 20 | 1 | 20 |
| chest | 36 | 1 | 36 |
| neck | 12 | 1 | 12 |
| head | 48 | 1 | 48 |
| arm_upper | 28 | 2 | 56 |
| arm_lower | 20 | 2 | 40 |
| hand | 16 | 2 | 32 |
| leg_thigh | 28 | 2 | 56 |
| leg_calf | 20 | 2 | 40 |
| foot | 16 | 2 | 32 |
| **Total** | | **17** | **400** |

The five central parts use 144 triangles. The six mirrored pairs use 256. Counting only the eleven authored files would give 272 and understate the assembled cost. This is why budgeting must follow actual instances.

## Construction strategy

The body uses a small number of shaped cross-sections, broad armor planes, a chamfered helmet, and closed triangular fin prisms. Hands use a simplified silhouette with painted finger separation. Boots use a five-point side profile extruded across their width. The head receives more geometry than an individual hand or foot because the helmet and fins carry identity.

The source generator preserves the original part attachment headers and builds new geometry around them. This allows existing poses to remain meaningful. The textures communicate bevels, seams, dark structural material, and broad light windows. The delivered material's apparent glow does not establish physical cavity depth or actual scene illumination.

## Recorded checks

| Check | Recorded result | Scope |
|---|---|---|
| Assembled triangle count | 400 | All 17 rigid slots |
| Original triangle count | 3,804 | Inspected BU24 source robot |
| Native loader | Passed | BU24 MechaAmazing.jar |
| Existing animation clips checked | 23 | Snapshot's inspected clip set |
| Poses checked | 483 | Joint-preservation validation |
| Maximum joint position change | 0 in the recorded report | Preserved rig interface |
| Blender/native FK comparison | About 1.008×10⁻⁵ maximum vertex difference | Six sampled frames, after basis conversion |
| Turntable | 120 frames, 30 fps, 4 seconds, 1280×720 H.264 | Rendered preview |

The joint test and vertex comparison are different checks. The former establishes the preserved attachment behavior in the inspected pose set. The latter checks the preview/export assembly against the MA transform calculation at selected times. Neither is a console hardware test.

## What still needed correction

The first version's torso UVs skewed central blue motifs toward the sides. A later review found stretched side panels and a rotated toe stripe on the boots. Both were mapping problems; their repairs preserved the 400-triangle geometry. The [UV case study](uv-repairs.md) explains the exact changes.

This is an important limit of structural validation: a mesh can have correct counts, winding, and pivots while its texture mapping is visibly poor. Visual inspection is part of completion, not a decorative extra after the “real” tests.

## Transferable lessons

Use a weighted part budget, preserve a known rig interface, and make low-count parts intentional. Keep texture art and mapping independently editable. Test new views after a positive preview. Do not equate unchanged joint positions with unchanged collision bounds when the shell changes. Treat this asset as one reproducible example rather than a universal humanoid template.

For source/report provenance and verification limits, see [the evidence ledger](../references/evidence-ledger.md).
