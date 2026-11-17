# Texture atlases and UV ownership

## Plan the image as an interface

An atlas is shared data between the artist, geometry generator, exporter, and runtime. Give each region a purpose and stable identity. Record which parts use it, its orientation, whether it is mirrored, and whether repetition is intentional. A numbered tile map is more maintainable than scattered numeric offsets with no legend.

A simple panel atlas can suit a rigid robot: armor colors, joints, visor, recesses, sole tread, and common trim. An organic creature often needs a more tailored unwrap to preserve face, belly, wing, and tail markings. Reusing the same square tile on every section can produce obvious repeated bands and erase the animal's anatomy.

## Allocate texels by visibility

Use the game's view to allocate resolution. Faces, eyes, important emblems, and central identity motifs usually need more than hidden soles. A large mesh surface may still deserve few texels if it has a uniform material. Match density where continuous details cross islands, and deliberately vary it where focal detail warrants the difference.

Test the delivered texture size, not just a high-resolution source. A 512×512 atlas with many small tiles can provide less usable face detail than a carefully allocated smaller atlas. State both total image size and the approximate dimensions of critical islands when reviewing readability.

## Handle tile bounds explicitly

For image dimensions W and H, a tile origin (x0,y0), and a usable interior size (a,b), map local coordinates s,t with a known image-origin convention:

```text
u = (x0 + padding_x + s * a) / W
v = (y0 + padding_y + t * b) / H
```

Decide whether these values refer to texel centers or boundaries for the sampler/export path being used. Do not add a half-texel correction blindly. Check edge samples in the target renderer. A coordinate near a tile edge can still bleed into its neighbor when filtering or mip levels average surrounding pixels.

## Padding is a sampling problem

Extrude the island's edge colors into the gutter rather than leaving a high-contrast empty background beside it. Test the lowest expected on-screen size. Mipmaps compress the gutter along with everything else, so a padding width adequate for a close view may fail at distance. A one-pixel seam can be a sampler problem even when the geometric UV edge is correct.

For nearest filtering, inspect pixel-scale jitter and staircase artifacts. For linear filtering, inspect blur and neighboring-color leakage. There is no universally best setting for every retro style; match the engine and intended art.

## Share deliberately

Mirrored islands save space for symmetric armor. They are unsuitable for directional text, asymmetric scars, numbered emblems, or deliberately different left/right features unless those elements use separate space. Repeating a trim is useful for a manufactured pattern, but repeating an entire tail segment texture can create false joints or bright rings where the design expects a continuous taper.

Separate palettes can share identical UV layout. Keep variants aligned and verify all delivered images have compatible dimensions and alpha behavior. Do not assume that a color replacement retains the contrast needed for eyes, borders, or light windows.

## Keep editable sources

Save layered raster, vector, or other editable masters when part of the workflow. Export the exact runtime PNGs from those sources and include only relevant variants in the asset package. An SVG or script is useful as a master, but the target engine still needs its supported image format.

When changing atlas layout, update every mesh that samples the moved region. When only correcting UVs, do not regenerate texture art unnecessarily. Record image hashes in a regression report if preserving the texture is part of the contract.
