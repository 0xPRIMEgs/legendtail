# Prompt: repair mapping without losing approved work

> Read guides/06-uv-mapping.md and case-studies/uv-repairs.md. Inspect the current model and texture to reproduce the reported UV defect. Preserve a baseline. Determine whether the problem comes from projection, polygon corner order, fan-center assignment, mirrored orientation, atlas packing, filtering, or export conversion. Remap the affected surfaces according to their actual geometry. Use shared physical-coordinate mapping where a graphic crosses surfaces. Preserve positions, topology, pivots, textures, and unrelated parts unless a necessary dependency is explained. Re-export and inspect the repaired close-up, the full model, and the mirrored counterpart. Verify the intended unchanged fields and deliver the corrected revision.

Supply the exact asset and symptom. For example: “The chest line bends outward at the fan center,” or “The toe stripe is sideways and the boot side is stretched.”

Do not apply the case study's numerical dimensions blindly. Derive the mapping from the current asset. A repair may use several surface projections; it should not force a whole curved object into one planar island.
