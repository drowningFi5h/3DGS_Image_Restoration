# Geometry-Guided 360° Image Restoration via 3D Gaussian Splatting

Official repository for the paper:

**Geometry-Guided 360° Image Restoration via 3D Gaussian Splatting: Reconstructing Corrupted Omnidirectional Sensor Data via Explicit Multi-View Volumetric Priors**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)]()

---

## Abstract

Omnidirectional cameras frequently suffer from sensor degradation, resulting in dead pixels, vertical line defects, and fixed-pattern noise that become highly visible in equirectangular projections. Conventional restoration techniques such as interpolation, inpainting, and generative image synthesis often fail to preserve geometric consistency, particularly in 360° imagery where spherical distortion and missing scene geometry present significant challenges.

This work introduces a geometry-guided restoration framework that reformulates image repair as a 3D scene reconstruction problem. By leveraging **3D Gaussian Splatting (3DGS)** as an explicit volumetric representation, the proposed pipeline reconstructs the underlying scene from neighboring uncorrupted viewpoints and synthesizes a geometrically consistent replacement for the corrupted frame.

Experimental evaluation demonstrates a **94.70% defect correction rate** and a **63.60 dB PSNR**, validating the effectiveness of geometry-aware restoration for omnidirectional imaging systems.

---

## Key Contributions

* Novel geometry-guided restoration framework for corrupted 360° imagery.
* Utilization of **3D Gaussian Splatting** as an explicit multi-view volumetric prior.
* Distortion-aware cubemap reprojection for seamless omnidirectional processing.
* Elimination of hallucination artifacts commonly introduced by generative approaches.
* High-fidelity restoration of sensor defects while preserving scene geometry.

---

## Method Overview

The restoration pipeline consists of four major stages:

### 1. Multi-View Data Acquisition

A circular-arc camera trajectory captures multiple overlapping viewpoints of the scene. Spatial redundancy from neighboring views provides information for reconstructing corrupted regions.

### 2. Volumetric Scene Optimization

A 3D Gaussian Splatting representation is optimized using only uncorrupted viewpoints. The resulting volumetric scene captures geometry, depth relationships, and high-frequency texture information.

### 3. Novel-View Reconstruction

The trained 3DGS model synthesizes a clean image from the exact pose corresponding to the corrupted frame, ensuring geometric consistency with the original scene.

### 4. Cubemap-Based Restoration

The synthesized frame is transformed into a cubemap representation to minimize polar distortion. Localized histogram matching and seam-aware blending are applied to ensure smooth transitions across cube faces.

---

## Pipeline

```text
Corrupted 360° Frame
          │
          ▼
Multi-View Capture Sequence
          │
          ▼
3D Gaussian Splatting Optimization
          │
          ▼
Novel View Synthesis
          │
          ▼
Cubemap Projection & Seam Correction
          │
          ▼
Restored 360° Image
```

---

## Results

| Metric                 | Value                 |
| ---------------------- | --------------------- |
| Defect Correction Rate | 94.70%                |
| PSNR                   | 63.60 dB              |
| Restoration Strategy   | Geometry-Guided       |
| Scene Representation   | 3D Gaussian Splatting |
| Projection Domain      | Cubemap               |

The proposed framework successfully reconstructs dense sensor corruption while maintaining structural integrity and geometric accuracy throughout the omnidirectional image.

---

## Why Geometry Matters

Most image restoration approaches operate directly in the image plane, treating missing pixels as a texture completion problem. While effective for conventional photographs, these methods often struggle with omnidirectional imagery due to spherical distortion and the absence of reliable scene geometry.

Our approach instead reconstructs the scene itself. By leveraging an explicit 3D representation, restoration becomes a physically grounded rendering problem rather than a generative estimation problem.

---

## Repository Contents

```text
.
├── README.md
└── paper.pdf
```

---

## Availability

The research manuscript is publicly available through this repository.

The implementation, automation pipeline, and supporting source code are currently undergoing proprietary review and are therefore not included in this release.

This repository serves as the official distribution platform for the research paper and associated architectural specifications.

---

---

## Authors

**Tausif Ansari**
Department of Computer Science and Engineering

**Shreetej Meshram**
Department of Information Technology

**Hamza Khan**
Department of Information Technology

---

## License

This repository is released under the MIT License.
