# Painting detail that earns its place

## Paint the cues that matter

A low-poly texture can describe bevel highlights, panel separation, shallow vents, knuckle divisions, tread, small bolts, material wear, eyes, and apparent recess borders. Use these cues to reinforce the geometry. A diagonal highlight that contradicts a straight physical edge can make a correctly modeled part look bent.

Begin with large color regions: armor, inner structure, visor/face, luminous elements, and optional accent. Check the figure in grayscale as well as color. If adjacent regions merge in value, a color difference alone may not survive the game background or downsampling.

## Establish a focal hierarchy

Reserve the sharpest contrast and most important detail for the face and key identity features. Let secondary areas be quieter. Covering every panel with equally bright lines makes the figure difficult to read. The design should remain recognizable when tiny markings disappear.

At severe budgets, the texture should support a simple, clear sculpture. It should not depict elaborate armor whose silhouette and occlusion contradict the underlying mesh. If a painted shape is repeatedly mistaken for an actual hole, either add depth or simplify the visual claim.

## Construct painted recesses carefully

Use a dark border to separate the opening from the plate, a restrained edge highlight to suggest thickness, and an inner color region with a clear shape. Keep the bright center away from the outer silhouette unless the structure actually reaches the edge. View under the runtime's shading model: baked highlights plus dynamic lighting can double-light the same surface.

For an unlit asset, painted value changes carry most of the form. For a lit asset, avoid baking strong directional highlights that rotate incorrectly with the object. Document which material path the texture was made for. A renderer's emission shader is a preview choice, not proof of engine emissive lighting.

## Give faces dedicated attention

Use a dedicated face/visor region when the character depends on it. Align eyes with the actual face geometry and check from three-quarter and side views. A face projected from a source illustration can inherit perspective, baked shadows, or background colors. Do not let a helmet edge cut through an eye because the source image and UV island disagree.

Design eye and mouth shapes to survive the delivered texture resolution. Keep enough space between high-contrast features to prevent them merging. Inspect mirrored faces for unintended asymmetry reversal. Small actual face planes can still be necessary for a nose, muzzle, cheek, or chin that must read in profile.

## Avoid camouflage repairs

Painting a missing surface the same color as the preview background can conceal a defect in one render and expose it immediately in game. Similarly, black paint cannot always replace a cavity: from a side view, the surface remains flat. Use truthful rendering and repair the relevant geometry or mapping.

## Review color variants as assets

Do not treat alternate palettes as a mechanical hue shift alone. Check contrast between joint and armor, visibility of the eyes, separation of light and trim, and readability on representative backgrounds. Keep any gameplay color coding distinct enough for its purpose. If glow is baked into the atlas, verify that a darker palette has not made the energy motif disappear.

## Finish with a small-scale test

Render at the intended character height with the actual filter settings. If a detail only survives in an enlarged still, either simplify it, enlarge its footprint, or remove it. Preserve editable art so those decisions remain cheap. Every additional painted line should help material, construction, or identity; visual noise is not a replacement for modeled quality.
