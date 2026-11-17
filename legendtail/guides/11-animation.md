# Animation that communicates character and impact

## Begin with the action's purpose

Describe what the motion must communicate: guarded readiness, relaxed confidence, a fast jab, a committed heavy swing, a stagger, or recovery. Identify the strongest pose and the important silhouette. Animation quality comes from readable intention, timing, spacing, balance, and follow-through; extra frames only sample those decisions more densely.

When using sprite references, identify the actual poses and events in each attack. Do not treat the sprites as a sequence of independent body proportions. Maintain one coherent 3D body and translate the illustrated exaggeration into pose, camera-readable silhouette, and timing. Do not invent missing attacks while claiming every source move was reproduced.

## Block before interpolating

Create anticipation, action, contact/release, follow-through, and recovery poses. Check them in the game's camera before adding intermediate keys. A sword should have a readable path, a kick should show the support leg's role, and a fireball release should have a visible emitting hand and release instant.

Use holds and changes in spacing deliberately. Evenly spaced rotations between every key often feel mechanical in the wrong way. A stylized robot can move sharply while still showing weight: brief preparation, quick extension, controlled recoil, and a clear return to guard.

## Example attack timing

This is a proposed 12-sample, 30 fps blocking pattern, not an inherited QuickFighter animation:

| Samples | Purpose | Review question |
|---|---|---|
| 0–2 | Anticipation | Is the upcoming direction readable without a long delay? |
| 3–5 | Acceleration | Does the striking limb lead a coherent body action? |
| 6 | Contact or release | Does the gameplay event match the visible pose? |
| 7–8 | Follow-through | Does the action feel committed without breaking balance? |
| 9–11 | Recovery | Does the final state connect cleanly to the intended next state? |

Twelve sampled frames at 30 fps occupy 0.4 seconds of video. Their timestamps commonly run from 0 to 11/30 seconds. The animation's playback/loop duration is a separate convention that must be documented; do not infer it from the last timestamp without checking the engine.

## Build distinctive idles

Choose a center of balance, guard height, torso angle, hand shape, and rhythm for each character. A swordsman might keep the weapon poised while shifting the supporting shoulder. A heavy robot may settle through hips and knees. A small creature may scan with its head while the torso remains stable. Avoid giving every character the same synchronized sine-wave bob.

Keep planted feet stable in world or model space as appropriate. If the idle intentionally steps, hops, or floats, make that intention readable. Unplanned foot sliding is not personality. Use small offsets among head, chest, arms, and accessories so the body does not move as a single rigid object.

## Light, heavy, and hit reactions

A light attack usually needs quick readability and a short recovery; a heavy attack can use more preparation and follow-through. The exact timing belongs to the game's combat design. Do not lengthen an attack merely to satisfy a minimum frame count; sample the desired duration appropriately.

A hit reaction should communicate direction and severity without permanently breaking the rig. Separate visual recoil from gameplay knockback when the game owns world movement. Test that recovery returns to the correct baseline rather than accumulating offsets. Distinct reactions can share structure while varying weight, reach, and amplitude.

## Rigid-part constraints

At elbows, knees, shoulders, and hips, inspect cuff clearance and exposed inner surfaces at extremes. A rigid armor piece cannot bend like skin. Solve the pose or geometry instead of smoothing weights onto an incompatible source rig. Check that hands retain their grip and that a weapon follows its socket through the full motion.

Use quaternion interpolation consistently. Equivalent quaternions with opposite signs can cause an unintended long interpolation path if handled naively. Normalize and follow the target animation conventions. The visual test remains necessary even when interpolation math is valid.

## Review transitions and evidence

Inspect at speed, slow motion, and frame by frame around contact. Test loop boundaries and transitions into and out of attacks. Check both sides and the game's actual camera. A turntable is useful for spatial review but can hide motion timing because the camera itself moves; include a fixed-camera action view when assessing animation quality.

Report clip names, sample/key counts, frame rate, duration, loop behavior, root-motion policy, and whether gameplay events were connected. Do not call ten duplicate poses a ten-frame attack. Preserve original timing when the user requests a faithful conversion.
