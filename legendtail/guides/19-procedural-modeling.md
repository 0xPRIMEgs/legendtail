# Procedural modeling with artistic control

## Code should express design decisions

A generator can make mesh construction repeatable, preserve pivots, and produce exact budgets. It cannot decide artistic quality merely by running successfully. Parameterize meaningful landmarks: shoulder width, waist taper, boot projection, helmet crown, fin angle, and section depths. Avoid exposing dozens of anonymous coordinates as the only way to revise a character.

Separate geometry, UV projection, material assignment, rig attachment data, export, and preview scene construction. This makes a UV-only fix possible without rebuilding unrelated systems. Keep the final asset deterministic when practical: the same source and parameters should produce the same model data.

## Use surface-aware abstractions

A generic loft helper can connect rings, but it should allow explicit per-surface UV functions and separate cap projections. The boot failure demonstrated why one default polygon map is insufficient. A side cap's UVs should derive from its profile coordinates, while the sole and toe need mappings based on their roles.

If a helper inserts a raised center vertex, it must ask the panel's projection function for that vertex's UV too. Averaging or hard-coding a texture center may work for a symmetric rectangle and fail for an asymmetric or tapered panel. Keep geometry generation and mapping coupled through named surface semantics.

## Guard assumptions locally

If a triangulation helper only supports convex planar polygons, assert or document that requirement. If a mesh writer expects triangle-list vertices, reject counts not divisible by three. If a projection divides by an extent, handle a zero-width surface deliberately. Keep count and bounds checks close to the operation that relies on them.

Do not hide missing data with a generic fallback that produces a plausible but wrong asset. A missing face island or connector should be a clear issue to resolve, not silently replaced with the first tile or root pivot.

## Iterate from renders

Generate a small set of diagnostic views quickly, inspect them, then adjust parameters or construction logic. Do not run an entire 160-creature batch before checking the family prototype. Use coarse preview settings for routine iteration, then final settings for delivery. Keep art decisions visible in comments or the brief so future revisions know why a section exists.

Procedural symmetry is useful, but break it intentionally where the character requires asymmetry. A random seed can make variants reproducible; it does not justify uncontrolled changes in anatomy or identity. Store the seed and parameters with the asset.

## Preserve reproducibility across exports

Record tool versions and explicit export settings that affect the result. Avoid relying on an editor's current selection, hidden modifiers, or prior scene state. Build or select the export set deliberately. Keep preview-only objects in a separate collection or equivalent grouping.

If the pipeline modifies a binary export after writing it, validate lengths, alignment, and references again. Prefer supported export configuration where available. A successful byte write is not proof that the modified file remains valid.

## Know when to stop generalizing

One strong character does not require a universal creature generator. Reuse proven helpers for sections, UV projection, rig preservation, and validation, while allowing asset-specific geometry. Generalize a repeated, understood operation after it has worked on representative cases. An abstraction that forces every torso into the same wedge has made the art worse even if it reduces code.

Document the small reproducible recipe and its limits. Keep an editable scene or clear parameter source so another artist can finish what code does poorly.
