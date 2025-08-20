This repository provides code for “Wisdom Tooth Detection in Panoramic Radiographs using Swin Transformer and Multi-Expert Consensus.”

It contains:
1. A 10-fold training and cross-validation notebook on panoramic radiographs which outputs a csv file with predictions and targets.
2. A metrics notebook that evaluates predictions per fold and computes aggregate results.
3. A csv file with image paths and labels
4. A folder containing 5505 panoramic images for training

---
Repository structure
```
.
├── train_10fold.ipynb       # Train and evaluate with 10-fold CV, outputs predictions CSV
├── Metrics.ipynb            # Load predictions CSV, compute metrics per fold and averaged
├── 5505-Dataset.csv         # Main dataset index: image paths and labels
├── data/                    # (optional) place images here if not absolute paths in CSV
├── outputs/                 # Stores predictions/targets CSV files
├── LICENSE
└── README.md
```
