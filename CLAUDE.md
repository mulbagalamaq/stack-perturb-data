---
description: 
alwaysApply: true
---

# CLAUDE.md

Guidance for Claude when working with this repository.

## Project Overview

Exploratory analysis using Arc Institute's **Stack** foundation model on **Perturb-Sapiens** single-cell perturbation data. The main work is in `explore_stack.ipynb`.

## Key Files

- `explore_stack.ipynb` - Main notebook with embedding generation and UMAP visualization
- `stack_umap.png` - UMAP of Stack embeddings colored by cell type/tissue
- `adsf_vs_pbs.png` - Comparison of ADSF (cytokine) vs PBS (control) conditions

## Data

- **Source**: [Perturb-Sapiens](https://huggingface.co/datasets/arcinstitute/Perturb-Sapiens)
- **ADSF dataset**: 513,870 cells × 15,012 genes
- **PBS dataset**: 460,848 cells × 15,012 genes

## Model

- **Stack-Large**: Arc Institute foundation model (~2.6GB checkpoint)
- **Embedding dim**: 1,600
- **Source**: [arcinstitute/Stack-Large](https://huggingface.co/arcinstitute/Stack-Large)

## Running the Notebook

Requires A100 GPU (80GB) and ~10GB temp storage.

```bash
pip install arc-stack scanpy huggingface_hub umap-learn matplotlib
jupyter notebook explore_stack.ipynb
```

## Workflow

1. Download Perturb-Sapiens data from HuggingFace to temp directory
2. Load Stack-Large model checkpoint
3. Generate cell embeddings with `model.get_latent_representation()`
4. Compute neighbors and UMAP on embeddings
5. Visualize by cell type, tissue, and perturbation condition
