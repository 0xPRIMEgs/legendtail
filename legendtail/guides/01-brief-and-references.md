# Briefs and reference sheets

## Turn a wish into visible requirements

“Make Xen in a Mega Man Legends kind of style” identifies a direction, but leaves important decisions open. Translate it into a description of forms and constraints: a comparatively large helmet, strong boots and forearms, broad readable armor planes, restrained surface noise, painted material transitions, a recognizable face opening, and the character's specific fins and blue energy pattern. Keep the reference character's identity separate from the stylistic treatment.

Write three lists: features that must survive, features that can be simplified, and features that can disappear at the smallest LOD. A distinctive head crest may be indispensable; individual finger joints usually are not at 400 triangles. The lists must come from this character and its game camera, not from a universal humanoid recipe.

## Resolve the reference set

Choose a primary reference and explain how other views constrain it. Independent generated views can disagree about shoulder width, the number of fins, the location of a light strip, or whether a back panel exists. Do not average incompatible pictures into an accidental design. Choose a coherent construction and record the decision.

For front/back/side sheets, align the ground line, crown height, pelvis, shoulder, elbow, knee, and ankle. Keep camera projection and scale consistent. A perspective side view with a foreshortened arm is not an orthographic blueprint. When asymmetry matters, obtain both left and right views; a single “side” can conceal a weapon attachment or ornament.

Record whether the sheet is a concept or a render of an existing mesh. Concept sheets propose appearance; they do not establish topology, hidden depth, UVs, pivots, or triangle counts. Use them as constraints, then verify the geometry separately.

## Establish a useful pose

A T-pose exposes arm length and attachment positions. An A-pose may be more useful for some deformation workflows. A rigid MA replacement must follow the verified rest conventions of its target rig; do not silently reposition pivots just to match a prettier reference pose. Show an additional neutral assembly render when the engine's part-local axes are unintuitive.

Avoid extreme fingers, toes, capes, or foreshortening that make the reference hard to measure. Hide no required body part behind another in the construction sheet. Keep dramatic action poses as supplementary personality references.

## Define the acceptance view

Record the expected on-screen height, camera distance/projection, lighting model, and backgrounds. At a tiny gameplay scale, the silhouette and broad color layout dominate. A full-screen turntable can reveal defects but should not become the only quality target. A cockpit asset has different priorities: visible forearms, hands, knees, and animation arcs may deserve more detail than an unseen back.

Choose deliverables explicitly: source scene, separate parts, GLB, textures, engine files, stills, video, or an archive. Clarify whether “400 triangles” means the body alone or includes weapons/effects. If no exception is specified, count the complete character's modeled parts and disclose accessories separately.

## Write prompts that reduce avoidable ambiguity

A useful prompt states the action, identity anchors, geometry budget, texture allowance, rig contract, and review evidence. It can be short because the project files carry the detailed interface. “Make it good” becomes useful when followed by observable checks such as “retain the helmet's side profile and show both sides with a numbered checker before final texture.”

Do not require the user to write a production manual. Extract the brief from the request, inspect available source, and make reasonable reversible choices. Use [the brief template](../templates/asset-brief.md) and [the prompt helper](../prompts/brief.md).
