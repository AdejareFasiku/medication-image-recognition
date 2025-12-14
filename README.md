Pill Medication Image Recognition

Pill identification via CLIP embeddings and nearest-neighbor search on NIH C3PI/RxImage, with EDA, evaluation, and interactive demos.

## Overview
This repository contains code, notebooks, and resources to build an image-based pill identification system using CLIP-style image embeddings and nearest-neighbor retrieval over the NIH C3PI/RxImage datasets. It includes exploratory data analysis (EDA), model evaluation, and interactive demo notebooks.

## Project structure
- notebooks/              # Jupyter notebooks for EDA, preprocessing, training, and demos
- src/                    # Python package (data loaders, processing, model wrappers)
- models/                 # saved models / placeholders
- requirements.txt        # Python dependencies
- LICENSE                 # MIT license
- .gitignore              # Python .gitignore template

## Getting started
1. Create and activate a virtual environment (recommended):

   python -m venv .venv
   source .venv/bin/activate

2. Install dependencies:

   pip install -r requirements.txt

3. Open the EDA notebook:

   jupyter lab

## Dataset
This project targets NIH C3PI/RxImage datasets (or similar pill image datasets). Ensure you have proper rights to use the dataset and follow any licensing restrictions.

## Usage
- Use notebooks/0-eda.ipynb to explore the dataset and build preprocessing pipelines.
- Use CLIP or similar image-language models to extract embeddings and store them for nearest-neighbor search (FAISS recommended).

## Tags
pill, medication, image-recognition, computer-vision, pytorch, tensorflow

## License
MIT
