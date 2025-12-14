# AI Pill Image Retrieval with CLIP & Nearest Neighbors

This project implements an **image-based pill identification system** using
the **NIH RxImage dataset** and **CLIP (ViT-B/32) image embeddings**.

Instead of traditional classification, the system embeds pill images into a
semantic vector space and performs **cosine similarity search** to retrieve the
most visually similar medications.

---

## Project Overview

The pipeline performs the following steps:

1. Load and preprocess pill images (1024px subset preferred)
2. Extract metadata such as NDC codes and drug names
3. Compute image statistics and exploratory visualizations
4. Generate CLIP image embeddings (ViT-B/32)
5. Build a nearest-neighbor similarity index (FAISS or sklearn)
6. Retrieve top-K visually similar pills for a query image
7. Evaluate retrieval performance using Recall@K and MRR
8. Provide an interactive demo and a lightweight inference API

This approach mirrors **real-world FDA / NIH pill identification systems**.

___

## Project structure
- notebooks/              # Jupyter notebooks for EDA, preprocessing, training, and demos
- src/                    # Python package (data loaders, processing, model wrappers)
- models/                 # saved models / placeholders
- requirements.txt        # Python dependencies
- LICENSE                 # MIT license
- .gitignore              # Python .gitignore template


---

## Dataset

- **Source:** NIH C3PI / RxImage Dataset
- **Image Types:** RXNAV and NLM
- **Resolution:** 1024px images preferred
- **Metadata:** NDC11 codes, drug names, image type

> The dataset itself is **not included** in this repository due to size and
licensing constraints.

---

## Model & Methodology

- **Embedding Model:** `openai/clip-vit-base-patch32`
- **Embedding Size:** 512 dimensions
- **Similarity Metric:** Cosine similarity
- **Indexing:**  
  - FAISS (inner product on normalized vectors) if available  
  - sklearn NearestNeighbors fallback

---

## Evaluation Metrics

The system uses **Leave-One-Out (LOO) evaluation** on NDCs with ≥2 images.

Reported metrics include:
- Recall@1
- Recall@5
- Recall@10
- Mean Reciprocal Rank (MRR)

Example results from the notebook:
- Recall@1 ≈ 0.13
- Recall@5 ≈ 0.26
- Recall@10 ≈ 0.32
- MRR ≈ 0.18

---

## Outputs

The pipeline generates:

- Image property distributions
- Sample pill image galleries
- CLIP embedding arrays (`.npy`)
- Similarity indices (FAISS / sklearn)
- Retrieval heatmaps
- Query + Top-K visual panels
- CSV files for evaluation and retrieval results

All outputs are saved under the `outputs/` directory.

---

## Interactive Demo

The notebook includes:
- Image upload or path-based querying
- Visualization of query image + retrieved matches
- CSV export of similarity scores and metadata

---

## Mini Inference API

A lightweight `PillRetrieval` class is provided to:
- Load embeddings and indices
- Embed new query images
- Perform top-K retrieval programmatically

This allows reuse outside the notebook (e.g., scripts or services).

---

## Disclaimer

This project is intended for **educational and research purposes only**.
It is **not a medical device** and should not be used for clinical decisions.

---

## License

Academic / Educational Use
