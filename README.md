### Repository info

This repository provides code for “Wisdom Tooth Detection in Panoramic Radiographs using Swin Transformer and Multi-Expert Consensus.”

It contains:
1. train_10fold.ipynb: A 10-fold training and cross-validation notebook on panoramic radiographs which outputs a csv file with predictions and targets.
2. compute_metrics.ipynb: A metrics notebook that evaluates predictions per fold and computes aggregate results.
3. 5505-Dataset.csv: A csv file with image paths and labels.
4. Images: A folder containing 5505 panoramic images in jpg format for training.

---

### Repository structure

```
.
├── train_10fold.ipynb       # Train and evaluate with 10-fold CV, outputs predictions CSV
├── Metrics.ipynb            # Load predictions CSV, compute metrics per fold and averaged
├── 5505-Dataset.csv         # Main dataset index: image paths and labels
├── images/                  # images folder
├── outputs/                 # Stores predictions/targets CSV files
├── LICENSE
└── README.md
```

---

### Dataset format

The dataset is provided via 5505-Dataset.csv, located in the repo root alongside the notebooks.

This CSV contains the following columns:
* ImagePaths: path to the panoramic images in the images folder.
* Right Upper-0, Left Upper-1, Left Lower-2, Right Lower-3: Each column here contains binary labels (0 = absent, 1 = present) for the corresponding wisdom tooth position.
The number after the dash (e.g., -0, -1, -2, -3) indicates the index of that position in the 4D Labels array.
* Labels: True labels in 4D array (e.g. [1, 0, 1, 1]). 

---

### Usage

1. Run train_10fold.ipynb for 10-fold training and cross-validation.
2. Run compute_metrics.ipynb with the csv output from train_10fold.ipynb.

**Note:** Experiments in the paper were run on 3 NVIDIA TITAN RTX GPUs (24 GB). Training on smaller GPUs may require reducing batch size or image resolution.

---

### Dependencies

See the import cells inside each notebook (train_10fold.ipynb and Metrics.ipynb) for exact package versions used. Core packages include:

train_10fold.ipynb
* torch
* albumentations
* transformers
* ProgressTable

compute_metrics.ipynb
* torch, torchmetrics

Environment
* Python 3.10.14
* CUDA 11.8
* NVIDIA TITAN RTX (24 GB) × 3

