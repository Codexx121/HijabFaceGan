# HijabGAN  
### Bias-Aware Synthetic Face Generation for Inclusive Biometrics

HijabGAN is a research-driven computer vision project focused on improving representation fairness in synthetic face datasets. It investigates how generative models inherit dataset bias and proposes a hybrid pipeline for generating synthetic identities with underrepresented cultural attributes such as the hijab.

This project combines **StyleGAN2-ADA**, **semantic segmentation**, and **pixel-space compositing** to create privacy-preserving synthetic face data that is more diverse and useful for training fair biometric systems.

---

## Overview

Modern face recognition systems often suffer from demographic and non-demographic bias due to imbalanced training data. While synthetic data offers a privacy-friendly alternative, generative models tend to reproduce the same biases found in their source datasets.

HijabGAN addresses a specific representation gap:

> Existing generative models struggle to reliably generate identities wearing hijabs without altering identity structure, ethnicity, or unrelated facial attributes.

To solve this, HijabGAN introduces a hybrid approach:

- **Phase I:** Latent space investigation using StyleGAN2-ADA  
- **Phase II:** Semantic segmentation + compositing pipeline  
- **Phase III:** Hardness-based validation for robust dataset curation

---

## Key Features

- Privacy-preserving synthetic identity generation  
- Improved representation of underrepresented facial coverings  
- Hybrid GAN + segmentation architecture  
- Hardness-aware dataset filtering  
- Fairness-oriented biometric dataset augmentation  
- Research-backed methodology

---

## Methodology

## 1. Latent Space Editing (Failure Analysis)

We first tested whether the concept of a hijab could be controlled through StyleGAN latent directions.

### Observation:

Latent traversals often caused:

- Identity drift  
- Gender changes  
- Ethnicity entanglement  
- Inconsistent hijab rendering

This confirms that models cannot reliably generate attributes absent or rare in training data.

---

## 2. Pixel-Space Hybrid Pipeline

Instead of forcing the GAN to invent missing attributes, HijabGAN treats the hijab as a transferable semantic object.

Pipeline:

1. Generate synthetic identity using StyleGAN2-ADA  
2. Segment hijab mask using U-Net (ResNet34 encoder)  
3. Composite hijab onto synthetic face  
4. Boundary blending  
5. Histogram matching  
6. Identity consistency filtering

---

## Architecture

### Generator
- StyleGAN2-ADA

### Segmentation Network
- U-Net  
- ResNet34 backbone

### Validation
- Binary attribute classifier  
- Hardness score bins

---

## Hardness Test

Generated images are categorized by classifier confidence:

| Category | Score Range | Description |
|--------|------------|------------|
| Easy | > 0.90 | Frontal pose, clear lighting |
| Medium | 0.70 - 0.90 | Normal variation |
| Hard | <= 0.70 | Shadows, occlusion, difficult cases |

Hard samples are intentionally retained to improve robustness.

---

## Results

- 5,000+ synthetic unique identities generated  
- Easy: 42%  
- Medium: 28%  
- Hard: 30%

This suggests improved diversity beyond conventional synthetic pipelines.

---

## Why This Matters

HijabGAN explores how AI systems can become more inclusive by addressing representation gaps that affect real-world applications such as:

- Face verification  
- Missing person identification  
- Access control systems  
- Fair biometric benchmarking

---

## Ethics

This repository promotes:

- Privacy-by-design synthetic data generation  
- Bias mitigation research  
- Inclusive AI development

This project is intended for research and fairness benchmarking purposes only.

---

## Repository Structure

```bash
HijabGAN/
│── README.md
│── paper/
│── src/
│── notebooks/
│── models/
│── datasets/
│── outputs/
│── requirements.txt
