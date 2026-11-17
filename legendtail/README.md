# Legendtail

**Make the character recognizable. Make the mesh explainable. Make the export prove it.**

Legendtail is a Markdown handbook and agent instruction pack for making stylized, low-poly game assets. It collects practical lessons from Xen, Rimekin, QuickFighter, Azure Oath, and the 400-triangle BlissFire3 robot workflow. Its strongest measured examples concern the BlissFire3 mesh, rig preservation, and torso/boot UV repairs. Broader character and animation guidance is identified as production guidance, not a claim that every earlier asset succeeded.

The focus is deliberately narrow: readable game silhouettes, useful topology, painted detail, dependable UVs, rigid part rigs, expressive movement, honest previews, and exports that survive contact with a game engine. It is particularly useful for constrained humanoid robots and creature rosters. It is not a sculpting encyclopedia, a model generator, or a guarantee of professional art from a single prompt.

## Start here

Give your agent this instruction alongside the actual project and references:

> Read LEGENDTAIL.md, then follow only the guides relevant to this asset. Inspect the existing model and target loader before changing it. Produce the requested files, render the actual exported geometry, and report measured counts and remaining limitations.

For a new asset, start with [the asset brief](templates/asset-brief.md). For a broken asset, start with [troubleshooting](guides/20-troubleshooting.md). For adopting these instructions in an existing project, see [INSTALL.md](INSTALL.md); preserve that project's existing rules.

## The operating rules

1. Preserve identity before adding detail. Judge the untextured silhouette at gameplay size.
2. Give triangles a job: silhouette, articulation, visible depth, or an essential shading transition.
3. Map texture coordinates from the actual surface. A five-sided boot is not a regular pentagon.
4. Treat pivots, attachment order, names, and coordinate bases as an asset interface.
5. Review front, back, both sides, three-quarter views, and movement. A good front render is insufficient.
6. Separate concept images, model renders, runtime captures, and measured validation.
7. Build one strong representative of each body family before scaling a roster.
8. Keep the source, deliverable, preview, and validation report tied to the same revision.

## Reading map

| Work | Read |
|---|---|
| Agent workflow and completion rules | [LEGENDTAIL.md](LEGENDTAIL.md), [AGENTS.md](AGENTS.md) |
| Translate a loose request into an asset | [Brief and references](guides/01-brief-and-references.md), [silhouette](guides/02-silhouette-and-proportion.md) |
| Choose and spend a triangle budget | [Budgets and LOD](guides/03-triangle-budgets-and-lod.md), [mesh construction](guides/04-mesh-construction.md) |
| Build armor with an inner frame | [Armor and recesses](guides/05-armor-and-inner-frame.md) |
| Prevent stretched or displaced details | [UV mapping](guides/06-uv-mapping.md), [atlas layout](guides/07-texture-atlases.md) |
| Make low-poly surfaces carry detail | [Texture painting](guides/08-painted-detail.md) |
| Keep MAHumanoidRig compatibility | [MA rig contract](guides/09-mahumanoidrig.md), [coordinates and mirroring](guides/10-coordinates-and-mirroring.md) |
| Animate with intent | [Animation](guides/11-animation.md), [weapons and effects](guides/13-weapons-and-effects.md) |
| Make diverse creatures | [Creature families](guides/12-creatures-and-rosters.md) |
| Export and prove the result | [Formats](guides/14-export-and-formats.md), [renders](guides/15-renders-and-turntables.md), [validation](guides/16-validation.md) |
| Ship to constrained hardware | [Runtime and retro targets](guides/17-runtime-and-retro-targets.md), [iteration and delivery](guides/18-iteration-and-delivery.md) |
| Author meshes with code | [Procedural modeling](guides/19-procedural-modeling.md) |
| Diagnose a failure | [Troubleshooting](guides/20-troubleshooting.md) |

## Worked lessons

- [A measured 400-triangle humanoid](case-studies/blissfire3-400.md): an exact part budget and the limits of what its tests prove.
- [Torso and boot UV repairs](case-studies/uv-repairs.md): projection equations, failure mechanisms, and regression checks.
- [Xen and Rimekin art direction](case-studies/xen-and-rimekin.md): preserving character identity, avoiding repeated generic bodies, and learning from mixed feedback.

## Reusable documents

| Templates | Task prompts |
|---|---|
| [Asset brief](templates/asset-brief.md) | [Improve a prompt](prompts/brief.md) |
| [Triangle budget](templates/triangle-budget.md) | [Build an asset](prompts/build.md) |
| [Rig contract](templates/rig-contract.md) | [Review an asset](prompts/review.md) |
| [Review report](templates/review-report.md) | [Repair UVs](prompts/repair-uv.md) |
| [Release manifest](templates/release-manifest.md) | [Build a roster](prompts/roster.md) |

## Scope and evidence

The instructions are portable Markdown. This repository does not register slash commands, install editor plugins, execute hooks, or install a personal skill. An agent must be able to read the files and use suitable modeling/export tools. The prompts work as ordinary task text.

Detailed technical values tied to MechaAmazing refer to the inspected **BU24 asset/loader snapshot**, not an assertion about every version of that library. The [evidence ledger](references/evidence-ledger.md) distinguishes inspected artifacts, user feedback, general guidance, and unverified targets. Consult [sources](references/sources.md) for external documentation and [the glossary](references/glossary.md) for terminology.

Ponytail inspired the use of a concise agent entry point backed by reusable instructions. Legendtail's modeling material is independently written; it does not copy Ponytail's prompt or claim its benchmark results. See [sources](references/sources.md).

Version: **0.1.0**. Original documentation is provided under [MIT](LICENSE.md). Referenced games, characters, tools, and third-party assets retain their own ownership and licenses; no game assets are bundled here.

For maintenance, see [CONTRIBUTING.md](CONTRIBUTING.md), [CHANGELOG.md](CHANGELOG.md), and this edition's [validation record](VALIDATION.md).
