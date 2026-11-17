# Renders and turntables as evidence

## Choose views to answer questions

Front and back views show symmetry, central motifs, and part distribution. Left and right views show depth, protrusions, seams, and asymmetry. Three-quarter views reveal how those surfaces connect. Close-ups expose repaired regions. A clay/wireframe view reveals construction that a painted material can obscure.

Use comparable scale, projection, pose, background, and lighting for before/after images. Changing all of them at once makes a repair difficult to judge. Orthographic views are useful for construction comparisons; perspective views help approximate the game camera. Label which is being used.

## Render the actual model

Generate inspection images from the delivered geometry and materials, or a source proven equivalent to them. Concept images belong in a separate category. Do not repaint a render to hide an asset defect and then present it as export evidence. If a beauty render uses additional effects, identify them.

For a UV repair, show the repaired area at useful scale and at least one full-model view. A close-up of one boot should be labeled as a close-up so it is not mistaken for the complete deliverable. Include both feet or the mirrored assembly in the full-model check.

## Define a complete orbit

For N unique video frames, sample the camera angle as:

```text
angle(i) = start_angle + 2*pi*i/N, for i = 0 ... N-1
```

This covers a complete cyclic orbit without duplicating the first view as the last frame. The next frame in a loop returns to the starting angle. If instead using N−1 in the denominator, the first and last samples coincide; that can be deliberate for a still sequence, but introduces a duplicate viewpoint in looping video.

Keep the camera aimed at a stable point around the character's visual center. Fit the full motion envelope, including weapon swings, antennas, wings, and lifted feet. Do not crop a feature during the orbit. A slightly elevated camera can reveal armor depth, but should not substitute for a true side inspection.

## Frame count is not frame rate

| Frames | Playback rate | Video duration |
|---:|---:|---:|
| 20 | 60 fps | 0.333… seconds |
| 60 | 30 fps | 2 seconds |
| 60 | 60 fps | 1 second |
| 120 | 30 fps | 4 seconds |
| 120 | 60 fps | 2 seconds |

Specify both. A request for “60f” usually describes a count, but the playback rate still determines how useful the inspection is. Three models per second with 20 frames each implies 60 fps if shown consecutively. Such a reel is a catalog browse, not a detailed approval pass.

## Separate camera movement from animation

Keep the camera orbit outside the character animation export. If the model idles during the orbit, state the idle's loop length and whether it repeats. Include a fixed-camera clip when judging attack timing. Camera motion can make a weak or stationary animation seem more active than it is.

Ensure foot-ground placement covers the full motion range. Preview stage geometry should not inflate the character's triangle count or appear in the game export. Keep labels out of the character's silhouette and make them useful: name, LOD, triangle count, frame count, or view type.

## Verify the encoded file

Wait for the render process to complete successfully before encoding. A directory containing 120 old frames is not proof that a new 120-frame render has finished. Use a clean output directory or verify current-run timestamps/logs and completion.

Check the encoded codec, dimensions, frame rate, decoded frame count, and duration. Inspect frames from several parts of the orbit and the loop transition. Confirm the clip contains every requested model in the intended order. A correctly encoded video can still contain the wrong asset revision.
