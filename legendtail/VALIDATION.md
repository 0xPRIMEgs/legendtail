# Validation record — 0.1.0

Prepared 2026-11-17. This record describes documentation and selected example checks performed while assembling Legendtail. It does not certify every modeling recommendation or platform.

## Documentation checks

- Checked relative Markdown links for existing, case-correct file targets.
- Checked that every Markdown document is reachable from README.md through local links.
- Checked fenced code blocks for balanced opening/closing fences.
- Scanned the public-facing documents for private workspace paths, account-specific file IDs, and environment-specific download links.
- Kept all delivered repository files in Markdown format.

## Recomputed example checks

- Recounted the inspected robot's assembled part geometry: **400 triangles**.
- Compared all **11 budget rows** with their actual part files and instance multipliers.
- Compared all **17 rig rows**, including names, parents, and connector indices, with the inspected assembly source.
- Checked the documented BU24 MAMESH length formula against **11 actual mesh files**.
- Recomputed the boot side/toe/heel height mapping error: approximately **2.9163×10⁻⁸** in stored UV coordinates.
- Checked the 16-triangle boot construction arithmetic, the 144+256 assembled budget, the proper-rotation determinant of the documented basis conversion, and the 120/30 = 4-second video arithmetic.

## Evidence reviewed, not newly executed

The inspected package's native loader/483-pose results, sampled Blender/MA transform comparison, torso regression report, and encoded video metadata were reviewed as existing evidence. They were not rerun as full engine or hardware tests for this documentation task. The package's authoring source copies were checked against the available matching source snapshot.

## Limits

No new character was modeled to benchmark the Legendtail prompts. No automatic host/plugin installation was performed. Current MechaAmazing APIs beyond the inspected BU24 snapshot were not certified. Console and Android runtime compatibility is a validation plan in the handbook, not a new test result.

The packaged archive is checked for integrity and for containing the intended Markdown files only. Review [the evidence ledger](references/evidence-ledger.md) for the source snapshot fingerprints and claim boundaries.
