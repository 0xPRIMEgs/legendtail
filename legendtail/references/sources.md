# Sources and attribution

Edition prepared on 2026-11-17. External documentation is linked for the reader; version-specific project behavior is grounded in the inspected asset snapshot described below. No external source is treated as an instruction to override the user's project.

## Structural inspiration

- [Ponytail repository](https://github.com/DietrichGebert/ponytail)
- [Ponytail AGENTS.md](https://github.com/DietrichGebert/ponytail/blob/main/AGENTS.md)
- [Ponytail's core prompt](https://github.com/DietrichGebert/ponytail/blob/main/skills/ponytail/SKILL.md)

Ponytail demonstrates a compact agent-facing entry point and supporting repository structure. Legendtail adopts that organizational idea for a different domain. Its modeling guidance is independently written. It does not reproduce Ponytail's prompt, include its code, claim affiliation, or reuse its benchmark claims. Legendtail's task prompts are ordinary Markdown rather than registered plugin commands.

## Format and tool references

| Source | Relevant use | Scope |
|---|---|---|
| [Blender 4.2 UV operators](https://docs.blender.org/manual/en/4.2/modeling/meshes/editing/uv.html) | Mapping methods, seams, projection, UV workflow | A specific manual version; menus/methods vary |
| [glTF 2.0 specification](https://registry.khronos.org/glTF/specs/2.0/glTF-2.0.html) | Primitive/accessor structure, skins, material and container semantics | Consult the normative specification for exporter implementation |
| [Khronos skinning tutorial](https://github.khronos.org/glTF-Tutorials/gltfTutorial/gltfTutorial_020_Skins.html) | Joint transforms and inverse bind interpretation | Explanatory example, not a replacement for the specification |
| [MechaAmazing repository](https://github.com/0xPRIMEgs/MechaAmazing) | Upstream project location supplied in the work history | Current repository contents were not retrieved for this edition; detailed MA claims below use BU24 instead |

These references support specific technical concepts. Most of Legendtail is original workflow guidance and synthesis of the inspected project work, not a paraphrase of a single manual. No private account or download links are required to use the handbook.

## Inspected project material

The corrected `BlissFire3_Robot_400.zip` supplied the authoring scripts, engine parts, textures, rig/animation assets, preview configuration, and validation reports used for the measured examples. The relevant internal paths were:

- `source/build_robot.py`: explicit geometry budget, part construction, atlas projections, and pivot-header preservation.
- `source/ma_asset.py`: inspected binary read layout, named assembly order, connector indices, mirroring, and forward transforms.
- `source/export_render.py`: rigid export assembly, coordinate conversion, animation sampling, and preview setup.
- `model_report.json`: weighted part budget and texture dimensions.
- `native_validation.json`: BU24 loader and joint-preservation checks.
- `blender_rig_validation.json`: sampled vertex comparison.
- `uv_revision.json`: torso mapping repair record.
- `feet_uv_revision.json`: boot mapping repair and unchanged-data comparison.
- `video_validation.json`: encoded turntable metadata.

Those files are provenance for the case studies, not bundled game assets or a dependency required to read Legendtail. The original game's code and artwork are not redistributed in this repository.

## Feedback and historical context

The user's modeling requests and feedback informed the sections about preserving Xen's identity, texture-led detail, Rimekin body families, sprite-based fighter animation, turnaround reviews, and checkpoint delivery. Historical requests alone were not counted as completed work. Retrieved summaries of old assistant claims were treated cautiously and were not promoted into fresh runtime validation.

See [the evidence ledger](evidence-ledger.md) for the distinction between measured results and production guidance.
