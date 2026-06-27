# COVID-19 Detection from Chest X-Ray using CNN-Transformer

A deep learning project for **binary COVID-19 detection** from chest X-ray images using a **CNN-Transformer hybrid architecture**. The model combines the strong local feature extraction capability of Convolutional Neural Networks (CNNs) with the global context modeling ability of Transformers to improve classification performance.

## Overview

Chest X-ray images contain both **local abnormalities** (such as ground-glass opacities and lung infiltrates) and **global relationships** between different lung regions. Traditional CNNs are effective at extracting local visual patterns, while Transformers excel at understanding long-range dependencies across the entire image.

This project integrates both approaches into a single architecture for accurate COVID-19 detection.

## Dataset

This project uses the **COVID-19 Radiography Database** from Kaggle.

**Dataset Link:**
https://www.kaggle.com/datasets/tawsifurrahman/covid19-radiography-database

Only the following classes are used:

- COVID
- Normal

The task is formulated as a **binary image classification** problem.

---

## Model Architecture

### CNN Feature Extractor (EfficientNetB0)

The CNN backbone is responsible for extracting **local visual features** from chest X-ray images.

Its responsibilities include:

- Learning edges and gradients in early layers
- Detecting textures and lung structures in intermediate layers
- Learning complex visual patterns in deeper layers
- Producing feature maps that represent important regions of the lungs

In short, the CNN learns:

> **"What visual patterns exist in each local region of the image."**

---

### Transformer Encoder

The feature maps produced by the CNN are divided into patches (tokens) before being processed by the Transformer.

The Transformer focuses on understanding the **global relationships** between these extracted features.

Its responsibilities include:

### Self-Attention Mechanism

The model learns relationships between different lung regions simultaneously.

For example:

- Whether opacity in the right lung is related to abnormalities in the left lung
- Whether multiple infected regions appear together

---

### Global Context Modeling

Instead of analyzing each region independently, the Transformer compares information across the entire image.

This enables the model to recognize infection patterns distributed throughout both lungs.

---

### Feature Importance Weighting

The attention mechanism automatically learns which lung regions contribute the most to COVID classification.

Regions containing abnormalities receive higher attention weights, allowing the model to focus on diagnostically important areas.

In summary, the Transformer learns:

> **"How visual patterns from different parts of the lungs are related to each other."**

---

## Training Pipeline

The project includes:

- Image preprocessing
- Data augmentation
  - Random Horizontal Flip
  - Random Rotation
  - Random Zoom
- EfficientNetB0 feature extraction
- Transformer encoder
- Hyperparameter tuning
- Stratified K-Fold Cross Validation
- Cosine Decay Learning Rate Scheduler
- Early Stopping
- Model Checkpointing

---

## Technologies Used

- Python
- TensorFlow / Keras
- EfficientNetB0
- Transformer Encoder
- NumPy
- Pandas
- Matplotlib
- Scikit-learn

---

## Project Structure

```
├── dataset/
├── notebooks/
│   └── COVID DETECTION USING DEEP LEARNING.ipynb
├── models/
├── results/
└── README.md
```
---

## Features

- Binary COVID-19 classification
- CNN-Transformer hybrid architecture
- EfficientNetB0 backbone
- Global self-attention mechanism
- Hyperparameter tuning
- Stratified K-Fold validation
- Learning rate scheduling
- Model checkpoint saving

---

## License

This project is intended for educational and research purposes only.

The dataset belongs to its original authors and is distributed through Kaggle.

---

## Acknowledgments

- COVID-19 Radiography Database (Kaggle)
- TensorFlow
- Keras
- EfficientNet
- Vision Transformer (ViT) research community
