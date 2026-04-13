

# 🧠 LIFEDIALBENCH: Evaluating Memory Capability in Continuous Lifelog Scenarios

<p align="center">
  <a href="[YOUR_ARXIV_LINK]"><img src="https://img.shields.io/badge/arXiv-Paper-red?logo=arxiv" /></a>
  <a href="[YOUR_GITHUB_URL]"><img src="https://img.shields.io/badge/GitHub-Code-black?logo=github" /></a>
  <img src="https://img.shields.io/badge/Dataset-Coming%20Soon-orange" />
  <img src="https://img.shields.io/badge/License-MIT-blue" />
</p>

> **Evaluating Memory Capability in Continuous Lifelog Scenario**  
> Jianjie Zheng\*, Zhichen Liu\*, Zhanyu Shen, Jingxiang Qu, Guanhua Chen†, Yile Wang, Yang Xu, Yang Liu, Sijie Cheng†  
> Southern University of Science and Technology · RayNeo.AI · Tsinghua University · Shenzhen University · Shanghai Jiao Tong University  
> (\* Equal contribution. † Corresponding authors.)

---

## 📌 Overview

Wearable devices such as smart glasses (e.g., Ray-Ban Meta, RayNeo V3/X3) and always-on recording machines enable continuous lifelogging of ambient conversations. This creates a fundamentally new challenge for memory systems — one that existing benchmarks, which focus on one-on-one chat or human-AI interactions, are ill-equipped to address.

We introduce **LIFEDIALBENCH**, a novel benchmark designed to evaluate long-term memory systems in realistic, continuous dialogue lifelog scenarios.

<p align="center">
  <img src="assets/teaser.png" width="600" />
</p>

---

## ✨ Key Features

- **Two Complementary Subsets**
  - 🎥 **EgoMem** — Built on real-world egocentric videos (derived from the EgoLife dataset), capturing naturalistic multi-party conversations in-the-wild.
  - 🏘️ **LifeMem** — Constructed from a simulated virtual community, providing rich, dense, and controllable long-term dialogue scenarios.

- **Hierarchical Synthesis Framework** — A principled pipeline for curating high-quality, temporally consistent dialogue lifelogs with human-in-the-loop review.

- **Online Evaluation Protocol** — A novel evaluation paradigm that strictly adheres to temporal causality, preventing temporal leakage and ensuring systems are assessed in a realistic streaming fashion.

---

## 🔍 Key Finding

> *Current sophisticated memory systems fail to outperform a simple RAG-based baseline.*

Our experiments reveal a **counterintuitive result**: over-designed memory structures and lossy compression strategies actively **hurt** performance in lifelog scenarios. This highlights the critical importance of **high-fidelity context preservation**.

---

## 📂 Dataset

> 🚧 **Coming Soon**
>
> The LIFEDIALBENCH dataset (EgoMem & LifeMem subsets) will be released here upon paper acceptance. Please ⭐ star this repo to stay updated.

The benchmark will include:

| Subset | Source | Setting |
|--------|--------|---------|
| **EgoMem** | Real-world egocentric video (EgoLife) | In-the-wild, multi-party conversations |
| **LifeMem** | Simulated virtual community | Controlled, long-horizon lifelog |

---

## 🚀 Getting Started

> 🚧 Code and evaluation scripts are coming soon.

```bash
# Clone the repository
git clone [YOUR_GITHUB_URL]
cd lifedialbench
```

Requirements and setup instructions will be provided upon release.

---

## 📊 Evaluation

We provide an **Online Evaluation Protocol** that simulates a streaming, temporally-ordered inference setting — in contrast to traditional offline protocols which risk temporal leakage.

Evaluation scripts and detailed instructions will be released alongside the dataset.

---

## 📖 Citation

If you find LIFEDIALBENCH useful in your research, please cite our paper:

```bibtex
@article{zheng2025lifedialbench,
  title     = {Evaluating Memory Capability in Continuous Lifelog Scenario},
  author    = {Zheng, Jianjie and Liu, Zhichen and Shen, Zhanyu and Qu, Jingxiang and
               Chen, Guanhua and Wang, Yile and Xu, Yang and Liu, Yang and Cheng, Sijie},
  journal   = {arXiv preprint},
  year      = {2026},
  url       = {[YOUR_ARXIV_LINK]}
}
```
