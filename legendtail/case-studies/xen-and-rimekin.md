# Case study: Xen, Rimekin, and the limits of a successful preview

## What the feedback establishes

The visible work history contains repeated requests to improve Xen, reduce triangle counts, and use textures to carry detail. A later 400-triangle Xen attempt received positive feedback, followed by a request to apply the improved approach to Rimekin. Roster previews also received positive feedback at one point and criticism of rough models later.

These observations establish that some revisions improved the user's perception and that quality remained uneven. They do not establish that every creature, LOD, animation, or platform port was completed or approved. This chapter extracts production lessons; it does not reconstruct missing asset measurements.

## Xen's identity and construction constraints

The reference brief emphasized a gray armored character with blue energy elements, a stylized adventure-game appearance, and a visible sense of an inner frame beneath armor. The distinctive helmet fins, face opening, strong forearms, large boots, and chest/back light motifs carry identity. Simplification must protect those relationships before tiny surface features.

The “inner, not outer” request matters. A line painted on a plate is not automatically an inner frame. At a severe budget, use actual depth selectively where the camera needs it and explicitly label painted approximations elsewhere. Do not let budget pressure silently change the requirement while retaining the same descriptive claim.

## Why a deliberate rebuild can help

A low-count model can improve when it is designed for its target budget instead of repeatedly decimated. Broad planes, intentional profile corners, dedicated facial/armor regions, and coherent UV islands give the texture a stable surface to describe. A larger triangle count with poor proportions and mapping can look worse than a simpler, better organized mesh.

That principle does not make 400 a magic number. The correct count depends on the brief, camera, articulation, and acceptable simplification. If the intended face, hands, or real cavities cannot survive, a higher budget may be justified. The useful lesson is controlled representation, not numerical austerity.

## Why roster production magnifies weaknesses

Reusable construction makes many assets possible, but a weak shared body, UV seam, or tail mapping repeats across the roster. A creature's profile can expose flattened facial features that a frontal sheet conceals. Thin details may disappear in rotation. Repeated texture tiles can add unwanted bands to tails, necks, and bodies.

The remedy is to classify by body family, prove representative meshes, and preserve individual identity anchors. Use the same validation machinery while allowing different topology and mapping. Shared process is valuable; a shared generic silhouette for every creature is not.

## Reference consistency is part of the problem

Independent generated front/back/side pictures can disagree. Independently generated body parts or sprite frames can drift in scale and perspective. A modeler must reconcile those differences into one coherent construction and label invented hidden details. Do not present a visually plausible sheet as evidence of a consistent underlying rig.

## Lessons for QuickFighter and Azure Oath requests

The work history also contains requests for sprite-based character motion, weapons/effects, minimum animation samples, 400-triangle characters, and game/platform integration. Those requests define useful workflow needs. They are not, by themselves, proof that all requested assets or ports were finished.

For sprite-based fighters, map each move to actual source poses and events. For a 2.5D game, check the gameplay camera as well as full rotation. For platform work, separate the asset export from a validated build. These lessons apply even where a particular project's final artifact was not inspected for this handbook.

## The durable rule

Keep the next iteration tied to a specific visible defect and preserve what improved. A positive front render should trigger broader inspection, not end it. A later complaint is useful evidence about the remaining gap. Use that evidence to improve the family template or individual asset without claiming the entire historical batch was either perfect or worthless.
