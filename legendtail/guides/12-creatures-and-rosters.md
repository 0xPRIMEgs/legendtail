# Creature families and large rosters

## Choose rigs from motion, not species count

A roster of 160 creatures does not necessarily need 160 rig types, but it also does not fit one humanoid template well. Group by topology, articulation, and movement: what supports the body, what bends, what reaches, and which appendages define the silhouette. Share a rig only when its joints and motion vocabulary support the creature without distorting its identity.

| Family | Structural needs | Common failure |
|---|---|---|
| Upright biped | Pelvis, torso, arms/forelimbs, two legs | Human posture forced onto every species |
| Heavy or hunched biped | Distinct shoulder/hip relationship, strong support legs | Head and torso become one pointed wedge |
| Quadruped | Separate front/rear support chains and body span | Four humanoid legs attached without gait logic |
| Bird | Wing articulation, beak, correct leg bends | Paper-thin wings and ambiguous backward joints |
| Frog or low crawler | Wide limb placement and crouched support | Humanoid knees and detached-looking limbs |
| Serpentine | Longitudinal segments and taper | Repeated texture bands and abrupt thickness steps |
| Fish or swimmer | Body bend, fins, tail propulsion | Unnecessary walking limbs or rigid swimming pose |
| Winged quadruped | Independent wing and leg chains if both move | Wings reuse arm joints needed for walking |
| Multi-legged creature | Repeated but independently phaseable chains | All legs move together or penetrate the body |
| Floating or amorphous form | Core motion plus selected appendages | Decorative bobbing replaces intended structure |

These are planning categories. A production roster may merge or split them after inspecting its designs. Do not announce a precise rig count before classifying the actual creatures.

## Prove representatives first

Pick one easy representative, one structurally typical member, and one edge case from a family. Establish mesh construction, UV strategy, rig interface, and a small motion set. Review them before generating the entire family. A flaw in one reusable template becomes a roster-wide problem when multiplied.

Use stable IDs and record reference completion separately from mesh completion. A generated reference sheet is not a finished model. A rendered model is not necessarily rig-tested. A package missing textures is not delivered. Use [the roster prompt](../prompts/roster.md) to keep status meaningful.

## Preserve species-specific identity

Choose three to five anchors per creature: head shape, body posture, major appendage, tail silhouette, and distinctive marking. Do not rely only on recoloring a common body. At 400 triangles, a single carefully shaped beak or horn can be more valuable than several generic body subdivisions.

Check the side view for muzzle depth, bird leg placement, frog haunches, tail attachment, and belly volume. Avoid thin protrusions that vanish or split into visible seams from oblique views. Simplify them into sturdier shapes when the target camera permits it; preserve essential negative spaces deliberately.

## Map long surfaces continuously

For a tapered tail or body tube, use longitudinal distance for one UV coordinate and a consistent cross-section parameter for the other, with a planned seam. Do not reset the full texture tile on every segment unless repeating bands are intentional. Watch tip compression and cap mapping; a tail can be structurally valid while its pattern becomes a bright starburst.

Organic markings need their own placement logic. A belly patch should follow the creature's underside, not whichever polygon happened to receive tile 3. Keep eyes and face regions explicit. Use family templates to share construction methods, not to overwrite individual design.

## Extend the rig system carefully

An optional extended-rig package can depend on a base rig library when its public interface supports that arrangement. Keep dependency direction one-way and version the attachment/pose contracts. Do not embed a second incompatible copy of the base classes. Verify the actual API before prescribing class names or constructors. The historical MAExtendedRigs idea is architectural context, not proof of a currently available release.

## Batch without hiding defects

Review small batches with consistent camera and lighting, then inspect outliers individually. A rapid 20-frame rotation can browse a roster but is too brief for detailed seam or animation approval. Keep full-size stills or slower individual reviews accessible. Later criticism of a batch remains valid even if an earlier preview looked better.
