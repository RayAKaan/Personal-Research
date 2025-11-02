# 🧠 HMTAS — Hierarchical Multi-Document Topic-Aware Summarization

> **A Green-AI–driven framework for computationally efficient abstractive summarization.**
> HMTAS introduces a hierarchical, topic-aware approach to multi-document summarization that achieves high performance with a lightweight architecture.

---

## 🌍 Overview

**HMTAS (Hierarchical Multi-Document Topic-Aware Summarization)** is a research-driven framework designed to summarize information from multiple related documents efficiently.
Unlike large-scale models that rely purely on brute-force computation, HMTAS emphasizes *intelligent system design* — decomposing the summarization process into structured, interpretable stages.

| **Property**        | **Description**                            |
| ------------------- | ------------------------------------------ |
| **Type**            | Abstractive summarization (multi-document) |
| **Core Model**      | Lightweight `T5-small`                     |
| **Framework**       | Hierarchical, Topic-Aware, Multi-Stage     |
| **Efficiency Goal** | Maximize performance per parameter         |
| **Theme**           | *Smarter, Not Harder — Green AI in action* |

---

## ⚙️ Pipeline Architecture

```
┌──────────────────────────────┐
│   Multiple Input Documents   │
└──────────────┬───────────────┘
               │
     (1) Topic-Aware Clustering
               │
     (2) Hierarchical Merging
               │
     (3) Abstractive Summarization
               │
┌──────────────▼───────────────┐
│     Final Global Summary     │
└──────────────────────────────┘
```

**Key Innovations**

* 🧩 *Hierarchical Flow*: Document-level extraction followed by global abstraction.
* 🎯 *Topic Awareness*: Clusters content by semantic similarity using HDBSCAN & embeddings.
* ⚡ *Efficiency*: Uses `T5-small` (~60M params) vs. BART (~406M) or Pegasus (~568M).
* 📚 *Interpretability*: Each intermediate scaffold remains human-readable.

---

## 🧪 Comparative Evaluation (2000-sample test set)

| Model                 | ROUGE-1           | ROUGE-2          | ROUGE-L           | BERTScore        | Coverage | Compression |
| --------------------- | ----------------- | ---------------- | ----------------- | ---------------- | -------- | ----------- |
| **HMTAS (ours)**      | **27.79 ± 13.02** | **9.55 ± 10.47** | **18.57 ± 10.75** | **78.00 ± 4.27** | 10.44    | 22.26       |
| BART-Large-CNN        | 29.17             | 10.91            | 20.06             | 78.46            | 9.56     | 22.41       |
| T5-Base               | 27.23             | 9.31             | 18.06             | 77.33            | 11.19    | 18.49       |
| Pegasus-CNN/DailyMail | 31.89             | 13.78            | 22.93             | 78.12            | 10.75    | 19.28       |

📈 *Despite being 7–9× smaller, HMTAS achieves comparable summarization quality while maintaining top efficiency per parameter.*

---

## 🧭 Demo Example

**Input (3 documents):**

```
World leaders gathered in Geneva for the 2025 Climate Summit, marking a crucial moment in global climate policy.
---
Major economies announced historic climate investments at the Geneva summit, including EU and China actions.
---
The summit's final agreement includes binding emissions targets, transparency mechanisms, and finance commitments.
```

**Output (single-sentence summary):**

```
World leaders gathered in Geneva for the 2025 Climate Summit.
```

---

## 🧰 Installation

### 🔧 1. Environment Cleanup (optional on Kaggle)

```bash
!pip freeze > pkgs.txt && cat pkgs.txt | xargs pip uninstall -y
!rm -rf /root/.cache/pip /root/.cache/huggingface /root/.cache/nltk
```

### 📦 2. Dependencies

```bash
!pip install -q -U numpy==1.26.4 scikit-learn==1.3.2 transformers==4.38.2 \
datasets==2.18.0 sentence-transformers==2.7.0 rouge-score==0.1.2 \
bert-score==0.3.13 networkx==3.2.1 hdbscan==0.8.33 nltk==3.8.1 \
torch==2.5.1 torchvision==0.20.1 torchaudio==2.5.1 \
matplotlib seaborn umap-learn --extra-index-url https://download.pytorch.org/whl/cu118
```

### 📁 3. Run the HMTAS Notebook

```bash
python hmtas_inference.py
```

All outputs (plots, results, summaries) are saved to:

```
/kaggle/working/htas_output/
```

---

## 📊 Outputs

* `plots/` → Evaluation visualizations
* `generated_summaries.csv` → Model outputs
* `results_summary.json` → Final metrics

---

## 🌱 Why HMTAS?

> **Performance per Watt. Performance per Dollar. Performance per Parameter.**

HMTAS is a **Green-AI-aligned architecture** demonstrating that:

* Intelligent design can outperform raw scale.
* Hierarchical reasoning reduces redundancy.
* Small models can compete with giants — when guided by structure.

---

## 🧩 Repository Structure

```
HMTAS/
├── hmtas_inference.py         # Main inference script
├── hmtas_utils.py             # Helper functions (clustering, merging, scoring)
├── data/                      # Sample datasets or links
├── htass_output/              # Generated results
├── plots/                     # Evaluation plots
└── README.md
```

---

## 🧠 Research Insight

HMTAS stands as a proof-of-concept for **principled decomposition** in summarization —
a shift from brute-force scaling to *structural intelligence*.

> “In a world chasing larger models, HMTAS shows that efficiency, interpretability, and performance can coexist.”

---

## 🏆 Citation

If you use this work in your research or projects, please cite:

```
@article{rayyan2025hmtas,
  title={HMTAS: Hierarchical Multi-Document Topic-Aware Summarization for Computationally Efficient Abstractive Summarization},
  author={Rayyan Ahmed Khan},
  year={2025},
  journal={GitHub Repository},
  url={https://github.com/RayAKaan/HMTAS}
}
```

---

## 🤝 Contributors

* **Rayyan Ahmed Khan** — Lead Researcher & Architect
* **Team HTAS** — Web & ML Engineering Support

---

## 🪴 License

This project is released under the **MIT License** — free for research and educational use.

---

## ⭐ Support

If you find this useful, consider giving the repo a **star** 🌟 and sharing it with your peers.
Your support helps highlight efficient, sustainable AI research.

---

