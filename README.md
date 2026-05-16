# 🧠 LifeDialBench: Evaluating Memory Capability in Continuous Lifelog Scenarios

<p align="center">
  <img src="assets/logo.png" alt="RayNeo Logo" width="160" />
</p>

<p align="center">
  <a href="https://arxiv.org/abs/2604.11182"><img src="https://img.shields.io/badge/arXiv-Paper-red?logo=arxiv" /></a>
  <img src="https://img.shields.io/badge/Dataset-In%20Repo-green" />
  <img src="https://img.shields.io/badge/License-MIT-blue" />
</p>

> **Evaluating Memory Capability in Continuous Lifelog Scenario**  
> Jianjie Zheng*, Zhichen Liu*, Zhanyu Shen, Jingxiang Qu, Guanhua Chen†, Yile Wang, Yang Xu, Yang Liu, Sijie Cheng†  
> Southern University of Science and Technology · RayNeo.AI · Tsinghua University · Shenzhen University · Shanghai Jiao Tong University  
> (* Equal contribution. † Corresponding authors.)

---

## 📦 What’s in this repo

- **`data/`** — Released benchmark JSON for **EgoMem** and **LifeMem** (see [Dataset](#dataset)).
- **Evaluation scripts & baselines** — Still 🚧 **coming soon** (will be added alongside clearer run instructions).

Please ⭐ **star this repo** for updates.

---

## 📌 Overview

Wearable devices such as smart glasses (e.g., Ray-Ban Meta, RayNeo V3/X3) and always-on recording machines enable continuous lifelogging of ambient conversations. This creates a fundamentally new challenge for memory systems — one that existing benchmarks, which focus on one-on-one chat or human-AI interactions, are ill-equipped to address.

We introduce **LifeDialBench**, a novel benchmark designed to evaluate long-term memory systems in realistic, continuous dialogue lifelog scenarios.

<p align="center">
  <img src="assets/intro.png" alt="Figure 1: Comparison between the lifelog scenario and the conventional chatting scenario" width="700" />
</p>

*Figure 1: Comparison between the microphone-always-on lifelog scenario and the conventional on-demand human-AI chatting scenario.*

---

## ✨ Key Features

- **Two Complementary Subsets**
  - 🎥 **EgoMem** — Built on real-world egocentric videos (derived from the EgoLife dataset), capturing naturalistic multi-party conversations in-the-wild.
  - 🏘️ **LifeMem** — Constructed from a simulated virtual community, providing rich, dense, and controllable long-term dialogue scenarios.
- **Hierarchical Synthesis Framework** — A principled pipeline for curating high-quality, temporally consistent dialogue lifelogs with human-in-the-loop review.
- **Online Evaluation Protocol** — A novel evaluation paradigm that strictly adheres to temporal causality, preventing temporal leakage and ensuring systems are assessed in a realistic streaming fashion.

<p align="center">
  <img src="assets/main.png" alt="Figure 2: LifeDialBench framework overview" width="700" />
</p>

*Figure 2: Overview of the LifeDialBench benchmark construction framework and online evaluation protocol.*

---

## 🔍 Key Finding

> *Current sophisticated memory systems fail to outperform a simple RAG-based baseline.*

Our experiments reveal a **counterintuitive result**: over-designed memory structures and lossy compression strategies actively **hurt** performance in lifelog scenarios. This highlights the critical importance of **high-fidelity context preservation**.

---

<a id="dataset"></a>

## 📂 Dataset

The released files live under **`data/`**:

| File            | Subset   | Lifelog sessions | Multiple-choice QA items |
| --------------- | -------- | ---------------- | ------------------------ |
| `data/EgoMem.json`  | **EgoMem**  | 6                | 939                      |
| `data/LifeMem.json` | **LifeMem** | 1                | 1,717                    |

Each file is a **JSON array** of lifelog sessions. One session has:

| Field            | Description |
| ---------------- | ----------- |
| `history_name`   | Identifier for the lifelog / protagonist viewpoint. |
| `chat_time`      | List of timestamps aligned with streaming chunks in `chat_history`. |
| `chat_history`   | Temporally ordered dialogue: a list of **chunks**, each chunk a list of `{ "speaker", "content" }` utterances. |
| `qa`             | Evaluation items for that session (see below). |

Each **`qa`** object contains:

| Field            | Description |
| ---------------- | ----------- |
| `question`       | Multiple-choice question text. |
| `options`        | Four strings `"A. …"` … `"D. …"`. |
| `golden_option`  | Correct letter (`"A"`–`"D"`). |
| `answer`         | Short gold answer string (optional helper for scoring/display). |
| `question_time`  | When the question is posed in the online protocol (date string). |
| `question_type`  | One of `single_event`, `event_detail`, `multi_event`, `time_query`. |
| `evidence_date`  | Supporting evidence window / date hint for the answer. |
| `timescale`      | Granularity label for evidence (e.g. `10min`, `day`). |

Background on subsets:


| Subset      | Source                                | Setting                                |
| ----------- | ------------------------------------- | -------------------------------------- |
| **EgoMem**  | Real-world egocentric video (EgoLife) | In-the-wild, multi-party conversations |
| **LifeMem** | Simulated virtual community           | Controlled, long-horizon lifelog       |


---

## 🚀 Getting Started

```bash
# Clone the repository
git clone https://github.com/qys77714/LifeDialBench.git
cd LifeDialBench
```

After cloning, load the benchmark from:

- `data/EgoMem.json`
- `data/LifeMem.json`

Evaluation code and dependency versions will be documented when the scoring pipeline is published.

---

## 📊 Evaluation

We provide an **Online Evaluation Protocol** that simulates a streaming, temporally-ordered inference setting — in contrast to traditional offline protocols which risk temporal leakage.

Automated evaluation scripts will be added to this repository in a future update; the dataset JSON above matches that protocol’s fields (`chat_time`, `chat_history`, `qa`, etc.).

---

## 📖 Citation

If you find LifeDialBench useful in your research, please cite our paper:

```bibtex
@article{zheng2026lifedialbench,
  title     = {Evaluating Memory Capability in Continuous Lifelog Scenario},
  author    = {Zheng, Jianjie and Liu, Zhichen and Shen, Zhanyu and Qu, Jingxiang and
               Chen, Guanhua and Wang, Yile and Xu, Yang and Liu, Yang and Cheng, Sijie},
  journal   = {arXiv preprint},
  year      = {2026},
  url       = {https://arxiv.org/abs/2604.11182}
}
```

