# FACM: Flow-Anchored Consistency Models

**Technical Presentation · 2025-08-21**

## Overview

Two documents cover the topic at different levels. The foundations deck connects diffusion SDEs and Fokker-Planck equations to probability flow ODEs, Continuous Normalizing Flows, Flow Matching, and consistency models. The paper-reading deck then focuses on FACM: using the instantaneous velocity learned by Flow Matching to anchor the average velocity used by a few-step consistency shortcut.

## What I Focused On

- Why SDEs and probability flow ODEs can share the same time-dependent marginals.
- How Flow Matching supervises an instantaneous velocity field without simulating a full trajectory.
- Why a consistency mapping can be interpreted as an average velocity over the remaining time.
- How FACM combines an FM anchor with a consistency shortcut in one model.
- Expanded-time and auxiliary-time conditioning, JVP-based training, and one- to two-step inference.

## Knowledge Map

```text
Diffusion SDE
    -> Fokker-Planck Equation
    -> Probability Flow ODE
    -> Continuous Normalizing Flow
    -> Flow Matching: instantaneous velocity
    -> Consistency Model: average velocity / shortcut
    -> FACM: anchor + shortcut
```

## Key Takeaways

1. The Fokker-Planck equation can be rewritten as a continuity equation, yielding a deterministic probability flow ODE with the same marginals as the diffusion SDE.
2. Flow Matching learns the local, instantaneous direction of transport, whereas a consistency model aims to predict a direct map toward the endpoint.
3. Under the presentation's parameterization, the consistency output acts like the remaining displacement divided by the remaining time: an average velocity.
4. The FACM paper argues that training only the shortcut objective leaves the instantaneous field weakly constrained and makes the self-referential derivative target unstable.
5. FACM uses one network for two tasks: Flow Matching provides the anchor and the consistency objective provides the shortcut.
6. Expanded-time conditioning separates the FM and CM objectives into adjacent time intervals; auxiliary-time conditioning provides an alternative without expanding the range.
7. A Jacobian-vector product computes the derivative along the trajectory direction needed by the continuous consistency relation.
8. Inference uses the consistency map directly for one step or applies a short schedule for two or more evaluations; the flow teacher is only needed during training.
9. The reported ablations attribute the main stability gain to retaining the Flow Matching anchor across different backbones.

## Materials

- [Foundations: diffusion, flow, and consistency](foundations.pdf) - 48 pages
- [Paper reading: FACM method and experiments](paper-reading.pdf) - 35 pages

## References

- Peng et al., [FACM: Flow-Anchored Consistency Models](https://arxiv.org/abs/2507.03738)
- Lipman et al., [Flow Matching for Generative Modeling](https://arxiv.org/abs/2210.02747)
- Song et al., [Consistency Models](https://arxiv.org/abs/2303.01469)
- Song et al., [Score-Based Generative Modeling through Stochastic Differential Equations](https://arxiv.org/abs/2011.13456)
- Chen et al., [Neural Ordinary Differential Equations](https://arxiv.org/abs/1806.07366)
