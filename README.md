# Food Classification and Segmentation

A multi-task deep learning model capable of classification and segmentation of food and ingredients in images.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Dataset](#dataset)
- [Model Architecture](#model-architecture)
- [Results](#results)
- [License](#license)

## Overview

This project focuses on recognizing food ingredients in images through both segmentation and multi-label classification. A shared ResNet-50 encoder supports two task-specific heads, enabling the system to generate pixel-level masks and ingredient labels for dietary and nutrition-related applications.

## Features

- Food image classification
- Semantic segmentation of food items
- Pre-trained models and training scripts
- Evaluation metrics and visualization tools

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/food-classification-and-segmentation.git
    cd food-classification-and-segmentation
    ```
2. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```

## Usage

Run the project.ipynb

## Dataset

This project uses the [FoodSeg103](https://xiongweiwu.github.io/foodseg103.html) dataset. Download [here](https://research.larc.smu.edu.sg/downloads/datarepo/FoodSeg103.zip).

## Model Architecture
The model uses a shared **ResNet-50 encoder** that feeds into two branches:

- **Segmentation head:** A DeepLabV3 decoder produces pixel-wise ingredient masks.

- **Classification head:** Global average pooling followed by a linear layer predicts multi-label ingredient classes.

Training uses both losses jointly (cross-entropy for segmentation and BCEWithLogits for classification).
The shared encoder is initialized from a single-task segmentation model to provide stable, spatially informed features.

### Multi-Task Model Architecture
<p align="center">
<img width="558" height="666" alt="image" src="https://github.com/user-attachments/assets/e57d6799-43d9-4dc4-a952-62adee34e8eb" />
</p>

## Results

### Segmentation:
Multi-task learning (MTL) achieves nearly identical segmentation performance to the single-task model. Pixel accuracy, mIoU, and Dice remain stable, indicating that segmentation benefits from strong dense supervision even when sharing the encoder.

### Classification:
Classification performance decreases in the multi-task setting, showing lower precision and F1 compared to the single-task classifier. This suggests the shared backbone prioritizes segmentation features over fine-grained class discrimination.

### Qualitative Outputs:
Visual samples show that MTL segmentation is comparable to the baseline, with slightly smoother boundaries in some cases.

### Sample output
<p align="center">
<img width="1521" height="397" alt="image" src="https://github.com/user-attachments/assets/bd1180f2-4197-4462-914d-ea18e923648e" />
</p>

### Performance comparison of single-task models and multi-task model
<p align="center">
<img width="666" height="92" alt="image" src="https://github.com/user-attachments/assets/8e188609-cf1a-439c-b126-5906e13137ea" />
</p>

    
## License
This project was created for educational purposes as part of a school assignment. It is not intended for public or commercial use.

