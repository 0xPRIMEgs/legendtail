# Weapons, projectiles, and attack effects

## Separate the asset roles

A sword, a projectile, a hand aura, a shield, and an impact flash have different needs. The sword needs a stable grip and readable edge profile. The projectile needs a recognizable shape and direction. An aura must follow the limb without hiding the attack. A shield needs an intentional facing and coverage. An impact flash needs correct timing and visibility.

Record whether each object is a rigid attachment, an independently moving mesh, a billboard, a particle effect, or a shader effect. Do not promise a technique the target renderer does not implement. A portable low-poly effect may use a small mesh and an unlit texture, but its appearance must still be tested in the engine.

## Budget and model the weapon's silhouette

For a sword, prioritize blade length, tip, guard, grip position, and enough thickness to survive side views. Small engravings and bevel highlights can be painted. Preserve the intended hand-to-guard relationship; a visually accurate sword with a misplaced origin will be difficult to animate.

Count weapon triangles separately and include them in the complete character budget when required. State whether the 400-triangle count describes the body alone or body plus equipped items. Do not silently exclude the most expensive accessory.

## Define attachment space

Place the grip/socket in a documented local frame. Decide whether the effect follows the hand's full orientation, position only, or an independently aimed direction. Apply transforms once. A fireball should stop inheriting the hand transform after release if the gameplay design treats it as a free projectile.

Test left/right facing and mirrored characters. A sword's blade direction, guard, or texture can become reversed when the whole avatar is mirrored. For asymmetric equipment, use a dedicated mirrored configuration or an explicit orientation correction verified in motion.

## Give effects a visible lifecycle

Specify startup, active phase, release/contact, and fade or removal. Match the visual event to the gameplay event. A fist that glows long before a hitbox becomes active may be intentional telegraphing; a glow that appears after the strike is usually a mismatch. Record the intended timing instead of letting an exporter choose it implicitly.

For projectiles, inspect from the firing direction and from the side. Avoid a fireball that looks like an opaque box or disappears edge-on. If using transparent cards, test culling, sorting, intersections, and overdraw. If using an opaque mesh, give its contour enough structure to communicate motion without relying on unavailable bloom.

## Keep gameplay bugs separate from modeling bugs

A projectile that fires only once, spawns in the wrong state, or fails to damage an opponent may be a gameplay/state issue rather than a mesh defect. A loader's “needs review” message may instead indicate a file/schema problem. Inspect the responsible layer before remaking the asset.

Collision shapes and hitboxes can use simpler representations than visual meshes. Their placement should follow the game's intended attack semantics, not every painted flame. Verify owner exclusion, release position, and lifetime in runtime tests when those behaviors are part of the task.

## Deliver a complete effect contract

Document the mesh/texture names, origin, facing axis, scale, material requirements, attachment or spawn frame, animation timing, and budget scope. Preview the effect in context with the character, not only against a dark studio background. A glow that reads well in isolation may obscure a hand or vanish on a bright arena.
