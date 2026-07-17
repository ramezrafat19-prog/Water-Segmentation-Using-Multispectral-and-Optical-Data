# 🌊 Water Segmentation Using Multispectral and Optical Data

A deep learning project for pixel-level water-body segmentation using 12-channel multispectral and optical imagery, featuring a U-Net architecture implemented from scratch with PyTorch.

## 📖 Overview

This project develops an end-to-end deep learning pipeline for accurately segmenting water bodies from multispectral and optical data. Unlike standard RGB-based segmentation, the model uses 12 spectral channels to capture richer information about the Earth's surface and improve the distinction between water and surrounding land-cover classes.

The pipeline includes dataset extraction, exploratory data analysis, visualization of all 12 spectral bands, binary mask analysis, per-channel normalization, synchronized data augmentation, model training, and pixel-level evaluation.

A U-Net architecture is implemented from scratch using PyTorch, supporting 12-channel input and producing a single-channel binary water segmentation mask.

The model was trained on 260 samples and evaluated on 46 validation samples, achieving a best validation IoU of **0.6664**.

## 🚀 Features

* 📦 ZIP Dataset Extraction
* 🔍 Dataset Structure Exploration
* 🛰️ 12-Channel Multispectral Data Processing
* 🌈 Individual Visualization of All 12 Spectral Bands
* 🗺️ Binary Water Mask Analysis
* ⚖️ Per-Channel Data Normalization
* 🔄 Synchronized Image and Mask Augmentation
* 📐 Train / Validation Split
* 🧠 U-Net Architecture Built from Scratch
* 🔢 12-Channel Input Support
* 🎯 Binary Pixel-Level Segmentation
* 💾 Best Model Checkpointing
* 📊 IoU Evaluation
* 🎯 Precision Evaluation
* 🔎 Recall Evaluation
* 📈 F1-Score Evaluation
* 🖼️ Segmentation Prediction Visualization

## 🛠️ Tech Stack

* Python
* PyTorch
* NumPy
* Matplotlib
* Scikit-learn
* Google Colab
* Google Drive

## 📂 Project Workflow

```text
ZIP Dataset
    │
    ▼
Dataset Extraction
    │
    ▼
Dataset Exploration
    │
    ▼
Visualize 12 Spectral Bands
    │
    ▼
Analyze Binary Masks
    │
    ▼
Train / Validation Split
    │
    ▼
Per-Channel Normalization
    │
    ▼
Synchronized Data Augmentation
    │
    ▼
PyTorch DataLoader
    │
    ▼
U-Net From Scratch
    │
    ▼
Model Training
    │
    ▼
Best Checkpoint Selection
    │
    ▼
Validation Evaluation
    │
    ▼
Prediction Visualization
```

## 🛰️ Multispectral Input

Unlike conventional RGB images, this project uses **12-channel multispectral and optical data**.

The input tensor shape is:

```text
(8, 12, 128, 128)
```

Where:

* `8` → Batch Size
* `12` → Spectral Channels
* `128 × 128` → Image Resolution

The additional spectral information helps the model distinguish water from visually similar surfaces such as:

* 🌱 Vegetation
* 🟤 Soil
* 🏢 Buildings
* 🛣️ Roads
* 🌑 Shadows

Each of the 12 spectral bands is visualized individually during the exploratory data analysis stage.

## 🔄 Data Augmentation

Spatial augmentation is applied only to the training data.

Implemented transformations include:

* ↔️ Random Horizontal Flip
* ↕️ Random Vertical Flip
* 🔄 Random 90° Rotation

The same transformation is applied simultaneously to the multispectral image and its corresponding segmentation mask to preserve pixel-level alignment.

```text
Training Data:
Normalization + Augmentation

Validation Data:
Normalization Only
```

## 🧠 Model Architecture

A U-Net architecture was implemented from scratch using PyTorch.

### 🔽 Encoder

Extracts increasingly complex spatial and spectral features using convolutional blocks and downsampling.

### 🔬 Bottleneck

Learns deep semantic representations of the multispectral input.

### 🔼 Decoder

Progressively reconstructs the original spatial resolution to produce a pixel-level segmentation map.

### 🔗 Skip Connections

Transfer high-resolution spatial information from the encoder to the decoder, helping preserve fine details and accurate water boundaries.

### 📤 Output

The model produces:

```text
torch.Size([8, 1, 128, 128])
```

Each pixel represents a binary prediction:

```text
0 → Non-Water
1 → Water
```

## 📊 Model Configuration

| Component          | Configuration |
| ------------------ | ------------- |
| Framework          | PyTorch       |
| Architecture       | U-Net         |
| Input Channels     | 12            |
| Output Channels    | 1             |
| Image Resolution   | 128 × 128     |
| Batch Size         | 8             |
| Training Samples   | 260           |
| Validation Samples | 46            |
| Parameters         | 7,768,577     |
| Initialization     | From Scratch  |

## 📈 Results

The best validation checkpoint achieved the following results:

| Metric       |      Score |
| ------------ | ---------: |
| 🟦 IoU       | **0.6664** |
| 🎯 Precision | **0.8974** |
| 🔍 Recall    | **0.7228** |
| ⚖️ F1-Score  | **0.7909** |

### 📌 Performance Summary

The model achieved a validation IoU of **0.6664**, demonstrating meaningful overlap between the predicted water regions and the ground-truth masks.

The high **Precision of 0.8974** indicates that the model produces highly reliable water predictions with relatively few false positives. The **Recall of 0.7228** shows that the model detects a substantial proportion of actual water pixels, although some water regions may remain undetected.

The resulting **F1-score of 0.7909** demonstrates a good balance between prediction reliability and water-region coverage.

## 📊 Evaluation Metrics

The model is evaluated using:

* Intersection over Union (IoU)
* Precision
* Recall
* F1-Score
* Ground Truth vs Prediction Visualization

## 🔮 Future Improvements

* 🧮 Combine Binary Cross-Entropy with Dice Loss
* ⚖️ Apply class-imbalance handling techniques
* 🔍 Perform spectral-band ablation studies
* 📈 Optimize the segmentation threshold
* 🧠 Experiment with Attention U-Net
* 🚀 Explore advanced segmentation architectures
* 🛰️ Investigate additional water indices such as NDWI
* 🗺️ Apply spatially-aware dataset splitting
* 📊 Increase the size of the training dataset

## 📚 Dataset

The dataset consists of 12-channel multispectral and optical image patches paired with binary water segmentation masks.

Each image has a spatial resolution of `128 × 128` pixels, and each pixel is classified as either:

```text
0 → Non-Water
1 → Water
```

## 👨‍💻 Author

**Ramez Rafat**

Software Engineering Student | Artificial Intelligence & Machine Learning Enthusiast

## ⭐ Support

If you found this project useful, consider giving it a ⭐ **Star on GitHub**!
