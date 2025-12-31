# DualCDM: Dual-Domain Conditional Diffusion Model for SAR-to-Optical Translation

This repository provides the official implementation of **DualCDM**, a **dual-domain conditional diffusion model** for SAR-to-optical image translation. DualCDM jointly constrains the denoising process in both the **spatial domain** and the **frequency domain**, aiming to reduce frequency bias and improve the reconstruction of textures and fine structures in generated optical images.

## Method Overview

Given a conditional SAR observation \(S\) and a diffusion timestep \(t\), DualCDM follows the standard noise-prediction diffusion paradigm and learns to predict the injected noise \(\epsilon\). In addition to a spatial-domain objective, DualCDM introduces **frequency-domain supervision** to explicitly regularize spectral distributions and enhance high-frequency details.

- **Spatial-domain loss**: Mean squared error (MSE) on predicted noise to stabilize diffusion training.
- **Frequency-domain losses**:
  1. A spectral constraint on noise to regularize frequency distributions and mitigate frequency bias.
  2. A spectral constraint on the **one-step reconstruction** to encourage faithful recovery of frequency-domain structures.

This dual-domain optimization enables the model to learn complementary priors in both domains, resulting in improved translation fidelity and perceptual quality.

## Dataset: S1S2

We provide the **S1S2 dataset**, containing **15 paired images** between:
- **Sentinel-1 GRD** (SAR)
- **Sentinel-2** optical bands **B/G/R/NIR**, with values ranging in **[0, 10000]**

### Download

- **OneDrive**: `https://1drv.ms/u/c/385a9abf2e902c6b/ESULyVdGMptItgGVW93F6GEBXKQqsZ1Y89bg7YANp4nVYA?e=yztiIP`
- **Baidu Netdisk**: `https://pan.baidu.com/s/13rYqENQUrcA1VFU3Efsuig` (code: `lekm`)

After downloading, please place the data under `data/S1S2/` and follow `data/README_DATA.md` for the expected directory structure.

