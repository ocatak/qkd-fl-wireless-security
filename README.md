# QKD-Secured Federated Learning for 6G Wireless Intelligence

This repository contains code, notebooks, outputs, and paper sources for **Quantum Key Distribution (QKD) secured federated learning (FL)** in next-generation wireless systems.

The project studies two core 6G tasks:
- **Channel Estimation** (CNN-based FL)
- **Radar Spectrum Sensing / Segmentation** (U-Net-based FL)

Secure aggregation is implemented with **pairwise additive masking** and **BB84-style protocol-level QKD key generation**.

---

## Publication

- **arXiv:** [Quantum Key Distribution Secured Federated Learning for Channel Estimation in Next Generation Networks](https://arxiv.org/abs/2603.15649)

If you use this repository, please cite the paper (citation block provided below).

---

## Repository Structure

- `QKD_FL_ChannelEstimation_Pairwise.ipynb`  
  Main notebook for channel-estimation experiments (TVT-style scalability with `K ∈ {3,10,20}`).

- `QKD_FL_RadarSensing_MDI_Pairwise.ipynb`  
  Main notebook for radar sensing / segmentation experiments (TVT-style scalability with `K ∈ {3,10,20}`).

- `outputs/`  
  Generated experiment outputs, including:
  - `results_summary.csv`
  - `results_rounds.csv`
  - publication-ready figures and tables (`pub/`, `figures/`)

- `pubs/`  
  LaTeX source for the paper:
  - `paper_main.tex`
  - section files (`introduction.tex`, `system_model.tex`, `experimental_results.tex`, `conclusion.tex`)
  - figure assets in `pubs/figures/`

- Additional notebooks (`Dataset_Visualization.ipynb`, `QKD_Federated_Learning.ipynb`, etc.) are included for supporting analysis and legacy experiments.

---

## What Is Implemented

### 1) Federated Learning Modes

Across both tasks, the notebooks support:
- `plain`: standard FL (no masking)
- `classical_sa`: pairwise secure aggregation with classical PRG-derived keys
- `qkd_sa`: pairwise secure aggregation with BB84-style QKD-derived keys

### 2) Scalability Study

Experiments are run for:
- Number of clients: `K ∈ {3, 10, 20}`
- FL rounds: task-specific (configured in notebooks)

### 3) Security Controls

- Per-round QBER estimation
- Abort logic when `QBER >= threshold`
- Masking/key-generation overhead tracking
- Threat-model outcome tables and round-level logs

---

## Quick Start

1. Open either main notebook:
   - `QKD_FL_ChannelEstimation_Pairwise.ipynb`
   - `QKD_FL_RadarSensing_MDI_Pairwise.ipynb`

2. Run cells in order:
   - imports and config
   - dataset loading
   - TVT experiment runner
   - publication-output section

3. Check outputs:
   - `outputs/channel_estimation/`
   - `outputs/radar_sensing/`

---

## Main Output Artifacts

Typical generated files include:
- `results_summary.csv`: final per-configuration metrics
- `results_rounds.csv`: round-level metrics
- learning-curve figures (per `K`)
- overhead plots (masking + key generation time)
- publication tables (utility/security cost, threat outcomes)

---

## LaTeX Paper Build

The manuscript source is under `pubs/`.

To compile:
1. Open `pubs/paper_main.tex` in your LaTeX environment.
2. Build with `pdflatex`/`latexmk` (and BibTeX as needed).

---

## Citation

```bibtex
@article{catak2026qkdfl,
  title   = {Quantum Key Distribution Secured Federated Learning for Channel Estimation in Next Generation Networks},
  author  = {Catak, Ferhat Ozgur},
  journal = {arXiv preprint arXiv:2603.15649},
  year    = {2026},
  url     = {https://arxiv.org/abs/2603.15649}
}
```

---

## Notes

- The QKD component is modeled at the **protocol level** (BB84 abstraction), not a full physical-layer quantum optical implementation.
- Paths and output folders are notebook-configurable; reruns may overwrite prior results.
