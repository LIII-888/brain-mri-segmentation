# Brain MRI Segmentation

A deep learning pipeline for brain MRI tumor segmentation with U-Net, Swin UNETR, and Mamba-based models.

This project implements a complete medical image segmentation workflow including data preprocessing, model training, evaluation, inference, and visualization.

---

## Overview

Brain tumor segmentation from MRI scans is an important task in medical image analysis.  
This repository provides a reproducible deep learning pipeline for brain MRI segmentation using modern deep learning models.

The project includes:

- MRI data preprocessing
- Deep learning segmentation models
- Training and evaluation pipelines
- Model inference
- Visualization of segmentation results

The implementation focuses on building an **engineering-level medical AI project** rather than a simple experimental script.

---

## Features

- Multi-modal brain MRI preprocessing
- NIfTI medical image support (.nii / .nii.gz)
- Baseline model: **U-Net**
- Transformer model: **Swin UNETR**
- Advanced architecture: **Mamba-based segmentation**
- Training and evaluation pipeline
- Dice / IoU / HD95 metrics
- Prediction visualization and overlay
- Command-line inference for MRI volumes

---

## Project Pipeline


MRI Data
->
Preprocessing
->
Model Training
->
Segmentation Prediction
->
Evaluation
->
Visualization


---

## Dataset

This project uses public brain MRI datasets such as:

**BraTS (Brain Tumor Segmentation Challenge)**

Each case typically contains multi-modal MRI:


T1
T1ce
T2
FLAIR
Segmentation Label


Example dataset structure:


data/raw/
case_001/
t1.nii.gz
t1ce.nii.gz
t2.nii.gz
flair.nii.gz
seg.nii.gz


---

## Installation

Clone the repository:


git clone https://github.com/yourname/brain-mri-segmentation.git

cd brain-mri-segmentation


Install dependencies:


pip install -r requirements.txt


---

## Training

Train U-Net baseline:


python -m src.trainers.train_unet --config configs/unet.yaml


Train Swin UNETR:


python -m src.trainers.train_swin_unetr --config configs/swin_unetr.yaml


Train Mamba-based model:


python -m src.trainers.train_mamba --config configs/mamba.yaml


---

## Inference

Run segmentation on a new MRI volume:


python -m src.inference.predict
--model swin_unetr
--checkpoint outputs/checkpoints/swin_unetr_best.pth
--input data/raw/case_001
--output outputs/predictions/case_001


The output will be a segmentation mask in NIfTI format.

---

## Evaluation

Evaluate segmentation performance:


python -m src.evaluation.evaluate
--pred_dir outputs/predictions
--gt_dir data/processed/labels


Metrics include:

- Dice coefficient
- Intersection over Union (IoU)
- HD95 (Hausdorff Distance)

---

## Visualization

Segmentation results can be visualized as overlay images.

Example:

- Original MRI slice
- Ground truth mask
- Predicted segmentation
- Overlay comparison

Visualization tools are provided in:


src/visualization/


---

## Results (Example)

| Model | Dice | IoU | HD95 |
|------|------|------|------|
| U-Net | 0.82 | 0.70 | 8.5 |
| Swin UNETR | 0.86 | 0.75 | 6.9 |
| Mamba-based | 0.87 | 0.76 | 6.5 |

*(Results will be updated during experiments.)*

---

## Project Structure


brain-mri-segmentation/

configs/
data/
notebooks/

src/
datasets/
preprocess/
models/
trainers/
inference/
evaluation/
visualization/
utils/

scripts/
outputs/
docs/


---

## Future Work

Future improvements may include:

- Advanced Mamba-based architectures
- Improved loss functions
- Semi-supervised segmentation
- 3D transformer-based segmentation
- Clinical workflow integration

---

## License

This project is released under the MIT License.

---

## Acknowledgements

This project is inspired by research in medical image segmentation and the Brain Tumor Segmentation (BraTS) challenge.
