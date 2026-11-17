# Evidence ledger

## Labels used in this handbook

| Label | Meaning | Appropriate wording |
|---|---|---|
| Inspected artifact | A file, source, or report was actually examined | “The inspected package records…” |
| Recomputed check | A calculation was repeated against the available data | “The weighted total is…” |
| User feedback | A preference or assessment from the work history | “The user preferred this revision…” |
| Production guidance | A recommended practice derived from engineering/art reasoning | “Use this as a starting workflow…” |
| Proposal | A suggested architecture or approach not established as implemented | “An extension package could…” |
| Untested target | No relevant current runtime/hardware evidence | “Not verified on this target…” |

Keep these labels conceptually distinct even when prose does not repeat them in every paragraph. A useful recommendation need not be a benchmark; a benchmark needs more evidence than an attractive example.

## Claims and their support

| Claim | Evidence | Boundary |
|---|---|---|
| Assembled replacement has 400 triangles | Part budget, mesh data, export reports | Includes mirrored body slots; excludes preview stage |
| Source BU24 robot had 3,804 triangles | Inspected report and native validation record | Historical source snapshot |
| Eleven authored files fill seventeen slots | Assembly source and weighted budget | Explicit mirroring in this workflow |
| Pivot headers were preserved | Source writer and recorded comparisons | Does not imply all mesh-derived bounds remain equal |
| Twenty-three clips/483 poses were checked | Native validation report | Recorded BU24 test, not a new test of all later MA versions |
| Blender preview agrees closely with MA transforms | Sampled vertex-error report | Six sampled frames and stated basis conversion |
| Torso graphics needed coherent UV mapping | Source projections, repair report, inspected revision history | Specific panels; not a universal unwrap method |
| Boot repair changed only UV data | Byte/data comparison record and source | Compared with the previous torso-corrected revision |
| Boot repair preserved 16 triangles per foot | Geometry and report | Specific boot profile |
| Turntable has 120 frames at 30 fps | Video metadata report | Renderer preview, not console capture |
| A later Xen iteration looked better to the user | Visible feedback | Does not approve every later asset |
| Rimekin quality feedback was mixed | Visible feedback and historical context | Do not equate batch praise with per-species completion |
| 400/3k/6k workflows can be useful | Production guidance | Not hardware limits or guaranteed quality tiers |
| Extended creature rigs may be separated from a base library | Architectural proposal | Verify actual API and packaging before implementation |

## Snapshot fingerprints

SHA-256 identifies the specific local artifact bytes inspected for the measured examples. These are provenance records, not public download locations.

| File | SHA-256 |
|---|---|
| BlissFire3_Robot_400.zip | `70cca0da702d1bdd273910a3b02be3c698fb1b9d320f33826b27170e11e058be` |
| foot.mamesh | `1667d8490803c9bee061a4c6531678f7dbcf89a267bd658d81da9fe5266b7ee0` |
| chest.mamesh | `172ed1b8844969981ef1eeb7e7bf7b5e6ac5250624f65ab3c9fabb2cb68ac02f` |
| feet_uv_revision.json | `d74aa48072306a221b8b93358a6e9d9de0ccbc4dea36157e2fd24dec3fb79868` |
| native_validation.json | `8487351872bfa8778b252ad8ee542d65be710f28f7f4e25a38dfeba13dca02ad` |

The asset archive was the corrected revision containing both torso and boot fixes. Authoring source copies were compared with the packaged source to avoid documenting an older working copy. The new handbook's checks are recorded separately in [VALIDATION.md](../VALIDATION.md).

## Limits of this edition

Legendtail has not been benchmarked as an agent product. Its prompts have not been demonstrated to guarantee a particular artistic improvement. The documentation checks establish internal consistency, links, and selected numerical examples; they do not turn all recommendations into experimental findings.

This edition did not newly test the robot on PSP, Dreamcast, N64, Android, or every current MechaAmazing backend. It did not inspect every historical Rimekin, QuickFighter, or Azure Oath asset. Those projects contribute request/feedback context where stated. The detailed binary and index tables intentionally remain scoped to BU24.

For future revisions, add a dated observation with the asset and tool version, input, method, result, and limitation. Do not silently upgrade an old inference into a measured fact.
