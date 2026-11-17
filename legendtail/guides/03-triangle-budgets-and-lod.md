# Triangle budgets and levels of detail

## Define what is counted

A triangle budget refers to final triangles, not authoring faces. A quad usually becomes two triangles. A simple polygon with n boundary vertices triangulates into n−2 triangles when validly triangulated without extra vertices. Export modifiers, mirrored copies, cavity walls, accessories, and duplicated visible surfaces can change the total.

Distinguish unique mesh storage from triangles drawn per character. Eleven authored left/central files can assemble into seventeen rendered parts. Count both sides. Also distinguish triangles from vertices: UV seams and hard normals can split exported vertices without increasing the number of triangles.

For the common 17-part MA humanoid, 400/17 is about 23.53 triangles per part, or 11.76 quads if everything were quad-derived. A closed cube uses 12 triangles. This arithmetic shows how restrictive 400 is; it is not an instruction to assign two cubes to every body part.

## Use budgets as design choices

| Target | Likely strategy | Main pressure |
|---|---|---|
| Around 400 triangles | Deliberate broad planes, rigid segments, texture-led surfaces | Identity and articulation compete for every edge |
| Around 3,000 triangles | More shaped sections, selective real cavities, better face and joint silhouettes | Avoid spending the gain on invisible subdivisions |
| Around 6,000 triangles | More selective roundness and anatomy, richer silhouettes and overlaps | Preserve the same style; detail alone does not improve it |

These are workflow descriptions, not platform limits or guarantees. A tiny background creature may need less; a prominent cockpit hand may need more. Choose from the game's camera, number of visible actors, material cost, and measured runtime.

## Allocate before modeling

Give each part a provisional count and a reason. Reserve more for identity-heavy parts and joints that will be exposed in action. Keep a working reserve for late discoveries, then deliberately assign or remove it. Check the weighted total after every structural change.

The measured BlissFire3 example used 144 triangles for the five central parts and 256 for six mirrored pairs. Its head received 48 while each foot received 16. That distribution worked as a constrained construction, not a universal best allocation. See the full [case study](../case-studies/blissfire3-400.md).

## Reduce by redesigning the representation

Begin by asking what the removed geometry represented. A row of vents may become paint. A cylindrical hinge may become a dark joint surface with a painted center. A real opening that reveals the inner frame may need to remain an opening. Remove hidden geometry only after checking animation and all required views; a surface hidden in a T-pose can become visible during a kick.

Simplification should preserve landmarks, material boundaries that affect silhouette, and the shape of major negative spaces. If automatic decimation rounds or erases them, rebuild those regions manually or procedurally. Reprojecting an old texture onto a radically different mesh can preserve the wrong visual cues; repaint or rebake where needed.

## Make each LOD a finished asset

Do not assume a 6k-to-3k-to-400 chain preserves everything automatically. Check each level independently for silhouette, UVs, joint gaps, weights, material settings, and export count. Shared rig and texture layout can simplify integration, but force them only when they remain useful. A dedicated 400-triangle atlas may be clearer than a compressed reuse of a detailed high-resolution unwrap.

If LOD switching will happen during play, compare identical poses and screen sizes. Look for head-size changes, disappearing fins, shifted light bands, or feet changing footprint. Keep attachment transforms stable. Document whether a transition requires a texture/material switch.

## Handle an impossible limit honestly

If a requested budget cannot preserve all mandatory features, prepare the best concrete version within the limit and identify the specific tradeoff. Do not silently deliver 612 triangles as “about 400” when 400 was a hard cap. If an extra budget would resolve a visible problem, explain what those triangles buy; do not use a higher count as a substitute for improving the design.
