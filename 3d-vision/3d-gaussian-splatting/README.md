# 3D Gaussian Splatting

**Technical Presentation · 2026-05-28**

## Overview

This presentation traces the pipeline from multi-view images and camera parameters to rendered-image supervision: explicit 3D Gaussians, camera projection, screen-space footprints, alpha blending, differentiable rendering, densification, and optimization. It then examines how later work extends Gaussian primitives to geometry, semantics, language, editing, generation, and mapping.

## What I Focused On

- The coordinate transformations that connect world-space Gaussians to image pixels.
- How a 3D covariance becomes a 2D elliptical footprint under local projection.
- Front-to-back alpha blending and visibility-aware color accumulation.
- The differentiable loop from rendered-image loss back to Gaussian parameters.
- Densification, pruning, initialization, and the gap between visual quality and geometric accuracy.
- How later work adds geometry, semantic, language, and identity features to the Gaussian representation.

## Knowledge Map

```text
Multi-view Images + Camera Parameters
    -> Explicit 3D Gaussians
    -> World-to-camera Transformation
    -> Perspective Projection
    -> 2D Gaussian Footprints
    -> Alpha Blending
    -> Differentiable Rendering
    -> Loss and Gaussian Optimization
    -> Novel-view Rendering
    -> Geometry / Semantics / Generation / Mapping
```

## Key Takeaways

1. 3DGS represents a scene explicitly with Gaussian primitives carrying position, scale, rotation, opacity, and view-dependent color.
2. Camera extrinsics transform Gaussian centers from world to camera coordinates; intrinsics and perspective division determine their image positions.
3. Projecting only a Gaussian center is insufficient: the covariance must also be transformed to determine the size, orientation, and softness of its screen-space footprint.
4. Parameterizing covariance through positive scales and rotation keeps it valid during optimization.
5. Multiple footprints are composited front to back; each contribution depends on its local opacity and the transmittance left by nearer Gaussians.
6. The renderer is differentiable, so image-space errors can update location, covariance, opacity, and color parameters.
7. Adaptive densification adds detail where gradients indicate under-representation, while pruning removes ineffective primitives.
8. High rendering quality does not guarantee accurate surfaces or depth, especially under sparse views, weak texture, reflections, or poor initialization.
9. Later methods attach depth, semantic, language, or identity features to Gaussians while retaining the explicit representation and renderer.
10. A useful way to compare later methods is to ask which Gaussian attributes they add and which part of initialization, training, or rendering they change.

## Material

- [3D Gaussian Splatting slides](slides.pdf) - 87 pages

## References

- Kerbl et al., [3D Gaussian Splatting for Real-Time Radiance Field Rendering](https://arxiv.org/abs/2308.04079)
- [Official 3D Gaussian Splatting project](https://repo-sam.inria.fr/fungraph/3d-gaussian-splatting/)
- Lei Mao, [Camera Intrinsics and Extrinsics](https://leimao.github.io/blog/Camera-Intrinsics-Extrinsics/)
- PyTorch3D, [Cameras](https://pytorch3d.org/docs/cameras)
- Hugging Face, [Introduction to 3D Gaussian Splatting](https://huggingface.co/blog/gaussian-splatting)
- Shi Yan, [How to Render a Single Gaussian Splat](https://shi-yan.github.io/how_to_render_a_single_gaussian_splat/)
- [Gaussian Splatting Notes](https://github.com/kwea123/gaussian_splatting_notes)
- [Awesome 3D Gaussian Splatting Applications](https://github.com/heshuting555/Awesome-3DGS-Applications)
