# JiT: Understanding Large-Patch Pixel-space DiT

**Technical Presentation · 2025-12-04**

## Overview

This presentation studies why a minimalist pixel-space Diffusion Transformer becomes difficult to train with large patches and high-dimensional tokens. It first reviews DDPM, ADM, VAEs, latent diffusion, and DiT, then examines JiT's prediction target, patch-size experiments, manifold-based explanation, comparisons with latent-space models, and limitations.

## What I Focused On

- The efficiency and information trade-off between pixel-space and latent-space diffusion.
- Why patchification reduces attention cost while increasing per-token dimensionality.
- The difference between predicting clean images, noise, and velocity.
- JiT's `x`-prediction with a velocity-space loss under rectified flow.
- How the manifold hypothesis and a fixed hidden dimension explain the large-patch training problem.
- What JiT does and does not imply about replacing VAE-based latent diffusion.

## Knowledge Map

```text
DDPM / ADM
    -> VAE and Latent Diffusion
    -> DiT and patch tokens
    -> Pixel-space diffusion
    -> Large patches and high-dimensional tokens
    -> x / epsilon / velocity prediction targets
    -> JiT: x-prediction + velocity loss
    -> Manifold explanation and empirical validation
```

## Key Takeaways

1. Latent diffusion gains efficiency through a learned bottleneck, but its VAE can lose detail and separates representation learning from diffusion training.
2. Pixel-space diffusion removes the external tokenizer and enables end-to-end learning, but exposes the model to much higher-dimensional inputs.
3. Larger patches reduce token count and quadratic attention cost, while rapidly increasing the raw dimension represented by each token.
4. When the patch dimension exceeds the Transformer hidden size, the input projection becomes a strong compression bottleneck.
5. The paper explains the result through a manifold view: clean images are concentrated near a lower-dimensional structure, while Gaussian noise fills the ambient high-dimensional space.
6. JiT outputs a clean-image prediction and evaluates it through an equivalent velocity-space loss in a rectified-flow formulation.
7. The reported experiments show that velocity prediction remains competitive for small patches, while clean-image prediction becomes substantially better for large patches.
8. Patch size, prediction target, model capacity, and data space must be evaluated together rather than treated as independent design choices.
9. JiT is best understood as a specialized recipe for large-patch pixel DiTs, not a universal argument that all diffusion models should use clean-image prediction.
10. Its simple patchify/unpatchify design remains computationally demanding and does not eliminate the representation and efficiency trade-offs that motivate latent diffusion.

## Material

- [JiT: Understanding Large-Patch Pixel-space DiT slides](slides.pdf) - 95 pages

## References

- Li and He, [Back to Basics: Let Denoising Generative Models Denoise](https://arxiv.org/abs/2511.13720)
- Peebles and Xie, [Scalable Diffusion Models with Transformers](https://arxiv.org/abs/2212.09748)
- Rombach et al., [High-Resolution Image Synthesis with Latent Diffusion Models](https://arxiv.org/abs/2112.10752)
- Ho et al., [Denoising Diffusion Probabilistic Models](https://arxiv.org/abs/2006.11239)
- Esser et al., [Scaling Rectified Flow Transformers for High-Resolution Image Synthesis](https://arxiv.org/abs/2403.03206)
