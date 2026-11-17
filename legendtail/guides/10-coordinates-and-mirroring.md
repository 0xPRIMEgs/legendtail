# Coordinates, pivots, and mirroring

## Name every space

Distinguish part-local geometry, attachment-local motion, assembled model space, engine world space, authoring-tool space, and export space. A vertex can be correct in one and wrong in another. Record axis directions, units, quaternion ordering, matrix convention, and whether transforms are stored or baked.

Do not assume “Y-up” describes every part's local long axis. In the inspected robot, different part constructions use different local directions, while their attachment frames assemble them into a coherent body. A calf's local Z and a thigh's local Y can both be intentional.

## Convert bases consistently

For a column-vector convention, let C convert old-space coordinates to new-space coordinates. Then positions convert as p_new = C p_old and rotations as R_new = C R_old C⁻¹. Apply the same basis change to geometry, attachment translations, orientations, and animation. Converting only vertices creates a model that looks plausible at rest but moves on the wrong axes.

For row-vector storage, transposes and multiplication order change. Do not mix formulas copied from different conventions. Write a tiny test with known basis vectors and a 90-degree rotation, then check it against the target implementation.

The BU24-to-Blender preview used the proper rotation (x,y,z) → (x,−z,y). Its determinant is +1, so that conversion alone does not reverse winding. Treat this as a snapshot-specific bridge, not an instruction to apply the same transform to every MA project.

## Reflect the complete interface

Reflecting across X uses M = diag(−1,1,1). Positions transform with M and orientations with M R M⁻¹. Because det(M) is negative, the geometry's handedness changes. Reverse each triangle's winding exactly once if that reflection is baked into positions, then handle normals consistently.

In the inspected xyzw quaternion representation, the corresponding orientation conversion can be represented as (qx,−qy,−qz,qw). This result depends on the stated reflection and convention. Verify it with basis vectors instead of generalizing the component signs to arbitrary mirrors.

Mirror child attachment positions and orientations as well as the shell. A visually mirrored thigh with an unmirrored knee connector will assemble or bend incorrectly. Also decide whether UVs should mirror the art or retain its direction. Printed lettering generally needs a separate treatment from symmetric armor color.

## Prevent double transforms

Common failures include mirroring in Blender and again in assembly, applying an object transform and also baking it into vertices, or multiplying a parent transform twice during export. Track the exact point where each operation occurs. Keep one canonical representation and derive export data from it.

Negative object scale can defer a reflection into the exporter or renderer. Do not assume it will be interpreted identically by every loader. Resolve it deliberately, preserving rig and normal semantics, and inspect the exported result with culling enabled.

## Test pivots with motion markers

Place a temporary axis marker at the pivot and an off-axis point on the part. Rotate through a known angle and observe the path. Check both the joint origin and the surface orientation. Two tests are needed because a wrong local rotation basis can preserve the pivot's position while rotating the part incorrectly.

Nonuniform scale after rotation can introduce shear when composed through a hierarchy. If the target rig assumes rigid transforms, bake shape changes into the mesh in the appropriate local space and preserve rigid attachment frames. Do not push scale into animation channels merely to compensate for a modeling error.

## Conversion checklist

Record one source-to-target transform, test cardinal axes, test one asymmetric pose, check winding and normals, check mirrored attachments, and verify round-trip or native transformed positions. If the rest pose passes and action fails, investigate frame composition before remodeling the visible shell.
