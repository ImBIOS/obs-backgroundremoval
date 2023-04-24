# OBS Background Removal Settings

- [Threshold](#threshold)
- [Contour filter](#contour-filter)
- [Smooth silhouette](#smooth-silhouette)
- [Feather blend silhouette](#feather-blend-silhouette)
- [Inference device](#inference-device)
- [Segmentation model](#segmentation-model)
- [Calculate mask every X frame](#calculate-mask-every-x-frame)
- [Blur background factor](#blur-background-factor)

## Threshold

Adjusts how much background to remove.

Behaviour of this setting varies based on the [segmentation model](#segmentation-model) selected:

- **SINet, MediaPipe:**  
  Lower values remove more of the image. The lowest setting will remove most or all of the image, while the highest removes nothing.
- **Selfie Segmentation, PPHumanSeg, Robust Video Matting:**  
  Higher values remove more of the image. The lowest setting will remove nothing, while the highest will remove most or all of the image.  

Changing this setting, along with the [segmentation model](#segmentation-model), may give a better background removal effect.

Default: `0.50`

## Contour filter

Reduces the amount of noise in the output by eliminating small face detections.

Excessively high (over around 25-50%) may break the background removal effect.

Setting to 0% will disable this option.

Default: `0.05` (5% of image)

## Smooth Silhouette

Asjusts how much smoothing to apply to the background mask.

Setting to `0` will cause a pixellated background removal effect.

Excessively high values may expose some background

Default: `0.50`

## Feather blend silhouette

Adjusts the transition between the background and portrait. Higher settings will give a smoother blend.

May significantly impact performance at high settings.

Default: `0` (off)

## Inference device

Sets whether to use the CPU or GPU for calculating the background mask.

This setting should be changed to GPU when possible, as this usually gives a significant performance boost over using the CPU.

Default: `CPU`

## Segmentation model

Selects the segmentation model to use from the following list:

- `SINet`
- `MediaPipe` (default)
- `Selfie Segmentation`
- `PPHumanSeg`
- `Robust Video Matting`

The model selected may have a significant impact on performance compared to others.

Changing this setting, along with the [background removal threshold](#threshold), may give a better background removal effect.

Default: `MediaPipe`

## Calculate mask every X frame

Adjusts how often the plugin should calculate a new background mask.

Setting this to `1` will cause every frame to be processed.

Setting this higher than `1` will cause some frames to be skipped, which may greatly reduce the CPU/GPU usage of the plugin, while also making the mask less "jittery".

For example, setting this to `2` will calculate a mask every 2 frames, `3` will calculate every 3 frames, etc.

Default: `1` (every frame)

## Blur background factor

Adjusts how much background blur to apply to the background. If set to `0`, the background will be made transparent instead.

May significantly impact performance at high settings.

Default: `0` (no background)
