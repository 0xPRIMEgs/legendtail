# Rig and loader contract

## Version and spaces

- Engine/library build or commit:
- Loader/serializer inspected:
- File magic/version, if relevant:
- Geometry units:
- Part-local axes and assembly/world axes:
- Quaternion component order:
- Matrix/vector convention and multiplication order:
- Authoring-to-export basis conversion:
- Mirroring owner: authoring, exporter, or runtime assembly; select the actual one.

## Part interface

| Rig slot/name | Source file | Parent | Parent connector index | Base frame | Child frames | Mirrored? |
|---|---|---|---:|---|---|---|
| Fill in | Fill in | Fill in | 0 | Record | Record | Specify |

Do not copy the BU24 table into a different rig without checking it. Add rows for all required parts and sockets. Specify optional or intentionally absent parts.

## Animation contract

- Required channel names and order:
- Pose translation/rotation spaces:
- Rest/bind pose behavior:
- Interpolation and normalization:
- Clip time units and loop convention:
- Root-motion owner:
- Rigid or blended weights:
- Per-instance state behavior:

## Preservation and verification

- Baseline asset hashes or version:
- Fields/bytes that must remain unchanged:
- Neutral assembly comparison:
- Asymmetric pose test:
- Existing clips and sampled times:
- Native/reference transform comparison and tolerance:
- CPU/GPU paths tested:
- Bounds/collision dependencies reviewed:
- Known untested paths:

Reference: [MA rig guide](../guides/09-mahumanoidrig.md) and [coordinate guide](../guides/10-coordinates-and-mirroring.md).
