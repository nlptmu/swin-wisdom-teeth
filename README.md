### Repository info

This repository provides code for “Wisdom Tooth Detection in Panoramic Radiographs using Swin Transformer and Multi-Expert Consensus.”

It contains:
1. train_10fold.ipynb: A 10-fold training and cross-validation notebook on panoramic radiographs which outputs a csv file with predictions and targets.
2. compute_metrics.ipynb: A metrics notebook that evaluates predictions per fold and computes aggregate results.

---

### Repository structure
To run the code, the project root should be organized as follows and must include a Dataset.csv file that indexes the images:
```
.
├── train_10fold.ipynb    # Train and evaluate with 10-fold CV, outputs predictions CSV
├── compute_metrics.ipynb # Load predictions CSV, compute metrics per fold and averaged
├── Dataset.csv           # Dataset index: image paths and corresponding labels
├── images/               # Folder containing all panoramic radiograph images in jpg format
├── outputs/              # Stores prediction/target CSVs, model weights, logs, etc.
├── LICENSE
└── README.md
```

---

### Dataset

The dataset analyzed in this study is not publicly available due to institutional and privacy restrictions. Access may be granted upon reasonable request to the corresponding author.

The dataset is not included in this repository. To run the code on your own dataset, you need to prepare a CSV file, Dataset.csv, with the following columns:

* ImagePaths: relative or absolute path to each panoramic radiograph image.
* Labels: ground-truth labels as a 4-element array, in the order:
  * Right Upper, Left Upper, Left Lower, Right Lower
  * Each element is binary (0 = absent, 1 = present).

Example:
```
ImagePaths,Labels
images/image1.jpg,[0,0,0,0]
images/image2.jpg,[1,1,1,1]
images/image3.jpg,[0,0,1,0]
```

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
* torch
* torchmetrics

Environment
* Python 3.10.14
* CUDA 11.8
* NVIDIA TITAN RTX (24 GB) × 3

---

### Citation

If you use this code or build upon it, please cite our paper:
```
@Article{swin-wisdom-tooth,
  author  = {Yung-Chun Chang, Chih-Hao Ku, Yoichi Ohiro, Dennis Chun-Yu Ho, Chih-Yuan Fang},
  title   = {Wisdom Tooth Detection in Panoramic Radiographs using Swin Transformer and Multi-Expert Consensus},
  journal = {Journal to be Assigned},
  year    = {2025}
}
```

---

### License
This project is licensed under the Apache-2.0 License - see the LICENSE file in the repository for details.
