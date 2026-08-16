# Diffusion, SDE, and Flow Foundations

**Learning Notes · 2025-07-17**

## Overview

These notes follow a path through the mathematical foundations of diffusion models. They begin with Brownian motion and the Wiener process, connect particle trajectories to probability-density evolution, and then move through reverse-time SDEs, score matching, probability flow ODEs, guidance, and an introduction to Flow Matching.

This curated learning document summarizes a public article series and adds short notes that connect the topics. The original PDF identifies its LLM-assisted summaries, and the references below link the source articles.

## What I Focused On

- Connecting microscopic random motion with macroscopic density evolution.
- Understanding SDE and ODE descriptions through Fokker-Planck and continuity equations.
- Seeing why reverse-time generation reduces to learning a score function.
- Relating stochastic diffusion sampling to deterministic probability flow ODEs.
- Building a conceptual bridge from diffusion models to Flow Matching.

## Knowledge Map

```text
Brownian Motion
    -> Wiener Process and Ito Calculus
    -> Stochastic Differential Equations
    -> Fokker-Planck Equation
    -> Reverse-time SDE
    -> Denoising Score Matching
    -> Probability Flow ODE
    -> Guidance
    -> Flow Matching
```

## Key Takeaways

1. The continuous limit of a random walk is modeled by a Wiener process, which provides the stochastic building block used by diffusion SDEs.
2. A Lagrangian view follows individual stochastic trajectories, while an Eulerian view tracks how the population density evolves.
3. SDEs and Fokker-Planck equations describe the same process at different levels: sample paths and probability densities.
4. Ito calculus keeps a second-order correction because Wiener increments scale differently from ordinary time increments.
5. Reverse-time SDEs introduce the score, `∇x log p_t(x)`, as the quantity needed to reverse diffusion.
6. Denoising score matching replaces an intractable marginal score with a tractable conditional objective under the forward perturbation process.
7. A probability flow ODE removes stochasticity while preserving the same time-dependent marginal distributions as the corresponding SDE.
8. Classifier and classifier-free guidance modify the sampling direction to trade diversity for stronger conditional alignment.
9. Flow Matching instead trains a deterministic velocity field that transports samples from a simple distribution to the data distribution.

## Material

- [Diffusion / SDE / Flow Matching learning notes](diffusion-sde-flow-notes.pdf)

## References

The main source is a 2025 WeChat article series by Sun Bingbing, supplemented by a Flow Matching lecture by cheern:

1. [From Brownian motion to the Wiener process](https://mp.weixin.qq.com/s/iyyui_SOGU3gj2UJ06Ukbw)
2. [Lagrangian and Eulerian views of diffusion](https://mp.weixin.qq.com/s/XKgtZhLm0TMKsmCkB7SEkg)
3. [SDE, ODE, Fokker-Planck, and Liouville equations](https://mp.weixin.qq.com/s/3TyrYG7jFtOAcG0kQZ148w)
4. [Ito integration and stochastic terms](https://mp.weixin.qq.com/s/oCTG08AqBF3TJtpgoT_stw)
5. [Forward and reverse diffusion processes](https://mp.weixin.qq.com/s/ZhjlJ29UQUnPVChD2BS9Nw)
6. [Reverse-time SDE](https://mp.weixin.qq.com/s/8y-OCj8_EzdoklfPyj-0Kw)
7. [Denoising score matching](https://mp.weixin.qq.com/s/Lbns01ZwEgu9DeaPlsrLMQ)
8. [VP-SDE](https://mp.weixin.qq.com/s/jVnvT80xDsjF6wPttHqrrQ)
9. [Probability flow ODE](https://mp.weixin.qq.com/s/OEh5NtOYZ-o4aCxenAAoOg)
10. [Classifier and classifier-free guidance](https://mp.weixin.qq.com/s/LHfRgh_tKPqA_Yvhq0Tmuw)
11. [Flow Matching introduction](https://mp.weixin.qq.com/s/n7VobD5yVnkTAzl6Ya4n9g)
12. [Generative AI Lecture 5: Guided Flow Matching](https://mp.weixin.qq.com/s/RNU0maaf_tkIA3w6a5w3EA)
