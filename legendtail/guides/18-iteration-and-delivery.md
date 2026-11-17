# Iteration, checkpoints, and delivery

## Preserve the approved baseline

Before an edit, identify the exact source revision and save a recoverable baseline. An asset's latest filename may not identify its latest contents. Track the model, textures, rig, animation, and preview together. Avoid overwriting a corrected chest while fixing a boot with an older working copy.

Write a short change intent: “remap foot sides, toe, heel, and sole; preserve geometry, pivots, textures, and prior torso mapping.” That sentence guides both the edit and the regression checks. If the repair needs a wider change, record why.

## Iterate by visible problem

Keep before/after comparisons at the same view and scale. Rank findings by impact and repair the highest-value issue first. A user's “looks better” is useful feedback but does not certify every part or platform. Continue to inspect new views and accept later criticism as evidence.

When a user requests a checkpoint ZIP, deliver a coherent snapshot before making the next reduction or redesign. Do not make them wait for a future improved version when the requested purpose is to preserve the current state.

## Keep generations and revisions separate

A new 400-triangle rebuild may have different topology and UVs from a previous decimated version. Give it a distinct revision or explanatory note. LOD variants should have explicit names and counts. Do not silently replace the high-quality source with the low-budget derivative.

For a roster, use one manifest with stable IDs and status fields. Count references, meshes, rigs, reviewed renders, and delivered packages separately. If 37 of 160 entries are actually packaged, report 37; do not count planned or partially generated entries as complete.

## Build a self-contained handoff

Include the requested engine files, portable model if requested, textures, editable source, and review media. Put each asset or port in a clearly named folder. Use relative paths and predictable names. Do not bundle unrelated backups or private workspace material simply because they are nearby.

Write a manifest with revision, triangle scope/count, texture dimensions, rig contract, animation information, validation performed, known limits, and install/copy paths. Keep it concise enough to use during integration. The detailed authoring source can explain how the asset was produced.

## Package after final validation

Wait for rendering and encoding to finish. Ensure the final source, exported model, preview, and reports all reflect the same revision. Exclude stale frame sequences, editor backup files, caches, and large intermediates unless requested. Test ZIP integrity and inspect the archive's internal paths.

When replacing assets in a full game backup, compare the archive against its baseline. List the files changed. A foot UV repair should not alter unrelated game code, fireball assets, or libraries. If a backup is older than the user's current project, provide an asset patch and clearly identify the backup version rather than presenting it as the latest game.

## Make downloads understandable

Use exact filenames and direct links supported by the delivery environment. Explain whether a ZIP is a model-only package, a game backup, source, or a platform build. A small preview image may be embedded for review, but should not be confused with the model itself.

If a link fails, verify the actual saved artifact and relink or repackage it without changing the asset unexpectedly. If saving or publication fails, say which result is ready locally and which external step did not complete. Do not claim a persistent download or published repository until it exists.

Use [the release manifest](../templates/release-manifest.md) for a repeatable handoff.
