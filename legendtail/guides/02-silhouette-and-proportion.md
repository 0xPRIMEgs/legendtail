# Silhouette, proportion, and character identity

## Start with relationships

A character is recognized by relationships among masses: head to torso, shoulder span to hips, forearm bulk to upper arm, boot length to calf, and ornament direction to body posture. Modeling each part attractively in isolation can still produce a weak assembled character. Review the whole figure whenever a major mass changes.

Use landmarks rather than a generic “human proportion” rule. A stylized robot can have an intentionally short waist and oversized boots; a quadruped can have a large skull and tiny pelvis. Compare the model with the chosen reference at matching scale. Measure broad ratios when your eye is uncertain, but do not mistake a ratio match for complete artistic fidelity.

## Inspect three kinds of shape

1. **Outer contour:** helmet crown, cheeks, chest taper, elbow and knee corners, toe projection, tail tip.
2. **Negative space:** clearance under an arm, gap between legs, opening inside a horn pair, wing/body separation.
3. **Internal mass division:** visor against helmet, chest against abdomen, armor against joint, muzzle against cranium.

Flat black silhouettes expose contour and negative-space problems. A three-value clay render exposes mass division. Use these before detailed textures; otherwise highlights can disguise weak geometry.

## Make the side view an equal partner

Many weak low-poly assets have a plausible front and a collapsed side: wafer-thin torsos, flat faces, short toes, or decorations aligned to the camera. Establish depth early. Compare the forehead, face opening, chin, chest projection, pelvis tilt, heel, and toe. For creatures, include muzzle depth, shoulder/rump masses, wing thickness, and tail attachment.

A feature that only exists as front-facing paint will disappear in profile. Decide whether that disappearance is acceptable at the target camera. If not, move vertices or reserve geometry for it.

## Break the primitive look deliberately

Boxes, prisms, and lofted rings are useful starting constructions. They need shaped transitions: different widths at joints and armor bulges, angled planes that follow the reference, and carefully located corners. Repeating one tapered prism for every limb produces a consistent but generic robot. Give each part a reason for its section changes.

At very low counts, choose a few strong planes. An extra edge that changes the cheek silhouette can matter more than several subdivisions on a broad, flat torso. Never spend the last triangles evenly just to make every part equally dense.

## Review at multiple sizes

Inspect a close view, the actual game size, and a smaller thumbnail. Close views reveal construction defects; gameplay views reveal whether the intended features survive; thumbnails expose competing focal points. Use a background that separates the dark suit from empty space, then test the actual game's backgrounds.

Check bilateral balance without assuming perfect symmetry is desirable. A weapon, damaged plate, hairstyle, or stance may intentionally break symmetry. Keep that design distinction while ensuring accidental export mirroring does not swap it.

## A practical correction sequence

If the character looks wrong, identify the largest mismatched relationship and change it first. Compare the same views before and after. Then correct secondary proportions and joint transitions. Only after that should you tune seam widths or small highlights. Record what the change improved and whether it created a new profile or clearance problem.

For a recognizable robot, a useful initial order is head/helmet, torso/waist relationship, shoulder span, boots, forearms, then secondary armor. For a creature, choose the order from its identity: a bird's beak and wing silhouette may outrank its torso detail. These are starting strategies, not mandatory anatomy laws.
