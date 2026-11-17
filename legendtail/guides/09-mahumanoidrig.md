# MAHumanoidRig as an asset contract

## Scope

This chapter documents the **inspected BlissFire3 BU24 pivot-based workflow**. It is not a promise that a newer MechaAmazing release has identical methods, indices, or file layout. Inspect the actual rig construction and loader before integrating. Historical descriptions involving MABone or MAModel must not override the pivot-based source being used.

The assembly has seventeen named slots, with eleven authored central/left mesh files. In the inspected construction, the right limbs are made by a mirroring step. That is an assembly behavior, not a claim that every MAHumanoidRig constructor automatically mirrors input.

## Verified assembly table

Indices below belong to this inspected part order. Child slots are indices on the parent part.

| Index | Rig slot | Source mesh stem | Parent slot | Parent child slot |
|---:|---|---|---|---:|
| 0 | groin | groin | root | — |
| 1 | abs | abs | groin | 0 |
| 2 | chest | chest | abs | 0 |
| 3 | neck | neck | chest | 0 |
| 4 | head | head | neck | 0 |
| 5 | leftUpperArm | arm_upper | chest | 1 |
| 6 | leftLowerArm | arm_lower | leftUpperArm | 0 |
| 7 | leftHand | hand | leftLowerArm | 0 |
| 8 | rightUpperArm | mirrored arm_upper | chest | 2 |
| 9 | rightLowerArm | mirrored arm_lower | rightUpperArm | 0 |
| 10 | rightHand | mirrored hand | rightLowerArm | 0 |
| 11 | leftThigh | leg_thigh | groin | 1 |
| 12 | leftCalf | leg_calf | leftThigh | 0 |
| 13 | leftFoot | foot | leftCalf | 0 |
| 14 | rightThigh | mirrored leg_thigh | groin | 2 |
| 15 | rightCalf | mirrored leg_calf | rightThigh | 0 |
| 16 | rightFoot | mirrored foot | rightCalf | 0 |

Names, parent relationships, and connector order are separate pieces of data. Correct names with wrong connectors still produce a broken rig. A correctly positioned rest pose can still rotate incorrectly if the local orientation is wrong.

## Preserve pivot frames

A part carries a base orientation and child attachment frames. Its geometry is interpreted relative to that interface. For a replacement intended to use existing animations, preserve the base/connector data and author the new surface around it. Do not recenter each mesh independently or apply a transform without updating the associated frame semantics.

The 400-triangle replacement preserved the original header bytes and verified unchanged joint positions across the inspected animation set. This is stronger evidence than aligning the model by eye. It does not prove every new surface avoids clipping, nor that collision volumes derived from mesh bounds remain identical.

## Use rigid weights when translating the rig

When exporting this part-based construction to a skinned format, assign each part's vertices to its corresponding joint with one effective weight of 1. Check every vertex and every required joint. Automatic smooth weights can deform armor or blend a boot into a calf in ways the source rig never intended.

A generic skinned GLB is not automatically MA-compatible. It needs a deliberate mapping back to the named parts, local frames, and loader-supported representation. Conversely, a collection of named part files does not establish a valid GLB bind pose without correct transforms.

## Test the interface through motion

Use an asymmetric test: one arm raised, the other forward; one knee bent, the other straight; head turned; torso twisted. Then sample existing clips at representative times, including extreme joint positions. Compare joint transforms or transformed vertices with the engine's native path when available.

Check root translation and orientation separately. A model can animate internally while drifting or rotating around the wrong world origin. Check CPU and GPU paths if the target supports both, since a cached GPU mesh may not reflect later changes automatically.

## Do not confuse asset state with fighter state

A shared mesh can be reused by several fighters, but their animation clocks, queued moves, and poses must be instance-specific or explicitly applied before each draw. Reusing geometry does not mean all fighters should share one mutable animation state. This is a runtime integration concern to verify in the current engine; this handbook does not prescribe an unverified method name.

Use [the rig contract template](../templates/rig-contract.md) to capture the actual project's version, axes, slots, and tests before editing.
