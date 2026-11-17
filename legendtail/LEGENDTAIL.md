# Legendtail — the modeling protocol

Use this protocol for creating, reducing, rigging, texturing, reviewing, animating, or exporting game assets. Follow the user's brief and the project's verified technical contract. Read this file first, then the relevant guide; do not load the whole handbook for a small UV repair.

## 1. Establish the asset contract

Record the subject, reference priority, intended game camera, triangle limit, texture limit, rig names and hierarchy, coordinate convention, animation needs, and deliverables. Inspect existing assets and the actual importer. A filename or an old chat description is insufficient evidence of a binary format.

When details are missing, inspect the project first. Make reversible artistic decisions and state meaningful assumptions. Ask only when an unresolved choice would change identity, compatibility, or a hard budget. Do not stall ordinary modeling work on optional preferences.

For an edit, save a baseline and identify the narrow change: UV coordinates, texture pixels, positions, topology, pivots, weights, or animation. Preserve other approved work unless a dependency requires changing it. Explain a dependency before broadening the edit.

Read: [brief](guides/01-brief-and-references.md), [rig contract](templates/rig-contract.md).

## 2. Solve the largest visible problem first

Rank defects by their effect on the actual view: identity and silhouette, proportion, pose, large color regions, surface mapping, then small detail. A pristine checker map cannot rescue the wrong head shape. More facial texture resolution cannot repair a profile with no muzzle or forehead volume.

Establish front and side volumes before decorative topology. Use simple masses for construction, then reshape them deliberately. Do not deliver an unedited stack of primitives as a finished character. Compare negative spaces and the relationship between neighboring parts.

For a style reference, translate it into concrete choices: head-to-body ratio, foot size, contour angularity, palette, texture density, joint exposure, and shading. A named style alone is not an executable design brief.

Read: [silhouette](guides/02-silhouette-and-proportion.md), [mesh construction](guides/04-mesh-construction.md).

## 3. Allocate geometry by function

Count the final triangulated asset, including mirrored instances, accessories, and visible cavity walls within the agreed scope. Budget each part before building. Keep a small working reserve, then report the exact final count.

Use geometry when removing it would alter a meaningful silhouette, motion, occlusion, or viewing-angle change. Use texture for seams, small bevel highlights, vents, finger separation, badges, and shallow surface layering when the game camera permits it. A texture cannot create a real opening or articulate a joint.

For a major reduction, re-author the silhouette and rebake/repaint as needed. Decimation is a candidate operation, not the quality criterion. Do not assume 400 triangles is appropriate for every character or platform.

Read: [budgets](guides/03-triangle-budgets-and-lod.md), [armor](guides/05-armor-and-inner-frame.md).

## 4. Make the surface mapping intentional

Choose UV projection by surface function. Keep flat graphic panels coherent across their triangles. Map generated center vertices with the same projection as boundary vertices. Use dedicated mappings for front, back, toe, heel, sole, and side panels where their roles differ.

Check with numbered, directional UV tests and the real art. Inspect the exported triangles with target filtering. Check seams, mirrored lettering, atlas gutters, and the side view. Never hide a hole or failed mapping with background-colored paint or a favorable camera.

Read: [UVs](guides/06-uv-mapping.md), [atlases](guides/07-texture-atlases.md), [UV case study](case-studies/uv-repairs.md).

## 5. Preserve the rig interface

Preserve verified part names, attachment indices, root orientation, local bases, and pivot positions for a drop-in replacement. Mirror geometry, attachments, orientation, winding, and UV intent together. Determine which layer performs mirroring; do not mirror twice.

For rigid parts, use one effective transform per vertex. Test a deliberately asymmetric pose and several existing clips. A neutral T-pose is a poor test of hierarchy errors. Geometry changes may affect mesh-derived collision bounds even when pivots are unchanged.

Read: [MAHumanoidRig](guides/09-mahumanoidrig.md), [coordinates](guides/10-coordinates-and-mirroring.md).

## 6. Give movement readable causes

Design anticipation, action, contact or release, follow-through, and recovery. Choose timing before increasing sample count. Character personality should change posture, rhythm, weight shifts, and guard position. Anchor weapons and effects to their intended space and synchronize their visible event with gameplay.

Review planted feet, joint intersections, root motion, loop continuity, and transition poses. Ten samples can document a poor motion just as faithfully as a good one. Sample count and frame rate must both be stated.

Read: [animation](guides/11-animation.md), [effects](guides/13-weapons-and-effects.md).

## 7. Verify the actual deliverable

Perform three distinct checks: visual quality, structural validity, and target-runtime compatibility. Use the exported asset for at least one readback inspection. A successful export only proves that a file was written.

Render front, back, left, right, and three-quarter views as relevant; include a close-up of the repaired region. For a turntable, state frames, rate, duration, and whether it contains animation. Keep preview stages and lighting out of the asset budget and export selection.

Inspect all requested LODs independently. For a roster, report counts by status: reference complete, mesh complete, rig tested, render reviewed, packaged. Do not turn a plan into a completion claim.

Read: [export](guides/14-export-and-formats.md), [validation](guides/16-validation.md), [delivery](guides/18-iteration-and-delivery.md).

## 8. Finish with reviewable evidence

Deliver the requested files, a short description of the visible change, measured budget, compatibility evidence, and any material limitation. Use concrete filenames and a clear revision. Keep editable source and textures when requested. Verify archive integrity and relative paths.

Label a concept image as a concept, a renderer preview as a preview, and an engine or hardware capture by its actual source. Never claim a generated image is evidence of a mesh, or imply hardware testing from a desktop render.

If the task requests only a review, do not silently modify the asset. If it requests a repair, complete the repair and the checks necessary to assess it. Continue within the authorized scope without adding approval gates for routine reversible steps.
