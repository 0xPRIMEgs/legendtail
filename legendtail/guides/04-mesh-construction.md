# Building useful low-poly topology

## Make each section purposeful

For rigid armor, a loft through a small number of cross-sections is often controllable: one section at the joint, one at the armor's widest region, and one at the taper or cuff. Each section should change the contour or support a required surface transition. Adding intermediate rings along a straight segment usually wastes the budget.

Vary cross-sections by purpose. A broad front plate with narrow side facets needs a different section from a rounded forearm or a wedge-shaped boot. Keep landmarks explicit in the authoring representation so later changes do not depend on searching anonymous vertex indices.

## Triangulate consciously

The triangle diagonal matters when a quad is twisted or its UVs do not correspond to a single affine surface mapping. Inspect the final diagonals in the export. Do not assume that an editor, exporter, and runtime choose the same split. For flat graphic panels, stabilize topology before painting or use a projection that remains consistent across either valid diagonal.

A fan from the first boundary vertex is suitable for a convex, planar polygon with consistent winding. It is not a general solution for concave outlines or holes. Use a suitable triangulator or divide the region into known convex pieces. A center fan spends extra triangles and can alter shading; reserve it for an actual raised/recessed center or a deliberate construction need.

## Keep surfaces valid

Check zero-area triangles, repeated vertices within a triangle, unintended duplicate faces, reversed winding, self-intersections, and non-finite coordinates. For a closed shell, each geometric edge should have two incident faces with opposite traversal directions. Compare geometric positions when testing a triangle soup; UV splits can duplicate vertex records without creating a real opening.

Choose tolerances relative to model scale. Welding everything within a large fixed epsilon can erase narrow windows or join adjacent fingers. A mesh can pass edge-incidence checks and still self-intersect, so supplement structural checks with visual inspection and targeted intersection checks when needed.

Not every asset must be closed. Foliage cards, a shield surface, or an intentionally open armor sleeve may be legitimate. Record the intended surface class and assess its backface behavior. Do not “repair” all open borders by adding inappropriate caps.

## Hide construction seams with structure

At articulated joints, overlap a cuff or joint core enough to prevent a view into empty space during expected poses. Avoid excessive overlap that visibly clips in compression. Test the motion range, including crouches and raised arms. A seam that is invisible in a neutral pose can become the dominant flaw in an attack.

Place the joint pivot where the intended movement occurs. A correctly shaped elbow rotating about the forearm's center is still wrong. Separate geometry placement from pivot placement and test both.

## Preserve shading intent

Flat shading makes plane structure visible; smooth shading interpolates normals and can make a very coarse form appear inflated or pinched. Select hard edges intentionally. A painted bevel on a broad flat face should not fight a smooth normal that implies an unrelated bulge.

Inspect with face culling enabled. Disabling culling can conceal reversed triangles and does not repair orientation. When mirroring or applying a negative scale, handle handedness and normals deliberately; see [mirroring](10-coordinates-and-mirroring.md).

## Useful construction checkpoints

After blocking masses, inspect front and side contours. After segmentation, test an extreme pose. After triangulation, inspect wireframe and a directional checker. After export, re-open the file and compare bounds, count, and material assignment. Each checkpoint should answer a different question; repeating the same beauty render is not a substitute.
