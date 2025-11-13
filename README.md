🧠 HMTAS — Hierarchical Multi-Document Topic-Aware Summarization
An advanced framework for enhancing abstractive summarization through intelligent content selection.
HMTAS uses a sophisticated pipeline to guide smaller models, enabling them to achieve summarization quality competitive with models 2-3x their size.

🌍 Overview
HMTAS (Hierarchical Multi-Document Topic-Aware Summarization) is a research-driven framework designed to improve the summarization of multiple related documents. Unlike approaches that rely solely on scaling up model size, HMTAS emphasizes structural intelligence—decomposing the task into a sophisticated, interpretable content selection pipeline that enhances a downstream abstractive model.

Property	Description
Type	Guided Abstractive Summarization (Multi-Document)
Base Model	FLAN-T5-Base (~250M parameters)
Framework	Hierarchical, Topic-Aware, Multi-Stage Content Selection
Efficiency Goal	Maximize summarization quality for a given model size
Theme	Smarter, Not Harder — Green AI in action
⚙️ Pipeline Architecture
HMTAS is not a model itself, but an advanced pre-processing strategy that creates a "guided input" for an existing abstractive summarizer.

text

┌──────────────────────────────┐
│   Multiple Input Documents   │
└──────────────┬───────────────┘
               │
(1) Sentence Extraction & Semantic Encoding
 (using `all-MiniLM-L12-v2`)
               │
(2) Topic Space Discovery
 (UMAP dimensionality reduction + HDBSCAN clustering)
               │
(3) Enhanced Content Selection
 (MMR with PageRank centrality, position, and diversity scoring)
               │
(4) Guided Input Assembly
 (Selected Sentences + Original Text)
               │
┌──────────────▼───────────────┐
│     Abstractive Summarizer     │
│       (e.g., FLAN-T5-Base)     │
└──────────────┬───────────────┘
               │
┌──────────────▼───────────────┐
│      Final Global Summary      │
└──────────────────────────────┘
Key Innovations

🧩 Principled Decomposition: Separates content selection from abstractive generation, allowing each stage to be optimized independently.
🎯 Advanced Topic Discovery: Uses UMAP and HDBSCAN to find meaningful semantic clusters in the source content, ensuring all key sub-topics are represented.
🥇 Sophisticated Scoring: Selects sentences using an enhanced MMR algorithm that considers relevance (PageRank), novelty (semantic coverage), position, and diversity.
⚡ Efficiency through Intelligence: By guiding a medium-sized model like FLAN-T5-Base, HMTAS achieves quality improvements without needing to train or serve a much larger model.
🧪 Comparative Evaluation (400-sample Multi-News test set)
The following results are the mean of 3 runs with different random seeds. The HMTAS component was first optimized on a validation set, and the best configuration was used for this final test.

Model	ROUGE-1	ROUGE-2	ROUGE-L	BERT F1	Coverage	Compression
FLAN-T5-Base	26.31	8.91	15.41	76.78	7.23	35.98
HMTAS(FLAN-T5-Base)	27.27	8.97	15.61	76.52	8.18	30.17
BART-Large-CNN	24.99	9.01	15.62	77.29	5.47	36.34
PEGASUS-CNNDM	26.37	9.28	15.82	76.35	7.04	32.74
📈 Finding: The HMTAS pipeline successfully enhances the base FLAN-T5-Base model, leading to improved ROUGE scores and significantly better source document coverage. While larger models like PEGASUS achieve the highest ROUGE-2/L scores, this experiment validates HMTAS as an effective method for boosting the performance of a given abstractive model.
