# 技术知识总结与分享

本仓库整理扩散模型、3D 视觉及其数学基础相关的学习笔记和技术分享。

内容按主题组织。每个条目保留原始材料、整理日期和一份简要的知识脉络。

## 学习时间线

| 日期 | 主题 | 方向 | 材料类型 |
| --- | --- | --- | --- |
| 2025-07-17 | [扩散模型、SDE 与 Flow 基础](diffusion-models/foundations/README.md) | 扩散模型 | 学习笔记 |
| 2025-08-21 | [FACM：Flow-Anchored Consistency Models](diffusion-models/facm/README.md) | Diffusion / Flow | 理论基础 + 论文阅读 |
| 2025-12-04 | [JiT：理解大 Patch 像素空间 DiT](diffusion-models/jit-pixel-dit/README.md) | 扩散模型 / DiT | 技术分享 |
| 2026-05-28 | [3D Gaussian Splatting](3d-vision/3d-gaussian-splatting/README.md) | 3D 视觉 | 技术分享 |

## 按方向整理

### 扩散模型

- [扩散模型、SDE 与 Flow 基础](diffusion-models/foundations/README.md) - 从布朗运动和随机微分方程出发，梳理 score matching、Probability Flow ODE 与 Flow Matching。
- [FACM](diffusion-models/facm/README.md) - 先梳理扩散、Flow 和一致性模型的理论背景，再集中阅读 FACM。
- [JiT：理解大 Patch 像素空间 DiT](diffusion-models/jit-pixel-dit/README.md) - 对比像素空间与潜空间扩散，讨论大 Patch、高维 token 和预测目标。

### 3D 视觉

- [3D Gaussian Splatting](3d-vision/3d-gaussian-splatting/README.md) - 相机几何、高斯投影、可微渲染、参数优化及后续应用。

## 关于材料

各主题 README 记录我对引用材料的理解，并提供原论文或参考资料链接。图表和引用观点均标注来源。

2025 年 7 月的笔记整理自公开文章；原 PDF 中标注了 LLM 辅助生成的总结及对应来源。
