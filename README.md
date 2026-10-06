# 🏥 Entity-Aware Medical Image Captioning

## 📌 Overview

This project presents an **Entity-Aware Medical Image Captioning System** that combines computer vision, Natural Language Processing, and Transformer-based architectures to generate clinically meaningful descriptions of medical images.

The system extracts visual information from radiological images and combines it with relevant medical entities identified through **PubMedBERT**. By incorporating both visual and textual information, the model generates captions that focus on important anatomical structures and clinical findings rather than producing generic image descriptions.

The project also includes **explainable AI techniques** to provide visual insights into the regions and features considered during caption generation.

---

## 📄 Research Publication

The work has been published as a research article in **IEEE Access**.

**Paper:** *Entity-Aware Medical Image Captioning*

- 🔗 **DOI:** [10.1109/ACCESS.2026.3716698](https://doi.org/10.1109/ACCESS.2026.3716698)
- 📖 **Journal:** IEEE Access, Volume 14, pp. 114457–114481
- 🏛️ **Publisher:** IEEE
- 📜 **License:** CC BY-NC-ND 4.0

---

## 🎯 Objectives

The main goals of the project are:

- **Medical Entity Extraction:** Identify relevant clinical entities such as anatomical structures and pathological findings from medical image captions.
- **Multimodal Caption Generation:** Combine visual image features with medical-language information to generate meaningful captions.
- **Context-Aware Understanding:** Incorporate domain-specific medical terminology using PubMedBERT.
- **Explainable Predictions:** Provide visual explanations through attention maps and region-of-interest visualizations.
- **Structured Output:** Present the generated information in a clear and clinically meaningful format.

---

## 🧠 Model Architecture

The proposed system combines a deep visual encoder, medical language representation, and Transformer-based caption decoder.

### Architecture Pipeline

```text
                ┌─────────────────────────┐
                │    Medical Image Input  │
                │   X-Ray / CT / MRI etc. │
                └────────────┬────────────┘
                             │
                             ▼
                ┌─────────────────────────┐
                │    DenseNet-121 CNN     │
                │   Visual Feature Maps   │
                └────────────┬────────────┘
                             │
                             │
                             ▼
                ┌─────────────────────────┐
                │   Multimodal Fusion     │
                │ Image + Medical Entities│
                └────────────┬────────────┘
                             ▲
                             │
                ┌────────────┴────────────┐
                │       PubMedBERT        │
                │ Medical Entity Features │
                └─────────────────────────┘
                             │
                             ▼
                ┌─────────────────────────┐
                │ Transformer Decoder     │
                │  Autoregressive Caption │
                │       Generation        │
                └────────────┬────────────┘
                             │
                             ▼
                ┌─────────────────────────┐
                │  Medical Image Caption  │
                └────────────┬────────────┘
                             │
                 ┌───────────┴───────────┐
                 ▼                       ▼
        ┌─────────────────┐      ┌──────────────────┐
        │ Entity Analysis │      │ Explainable AI   │
        │                 │      │ Attention / ROI  │
        └─────────────────┘      └──────────────────┘
```

### Main Components

#### 1. Visual Feature Encoder

**DenseNet-121** is used to extract high-level visual representations from medical images.

The extracted feature maps provide spatial information that is passed to the caption generation component.

#### 2. Medical Entity Representation

The NLP component uses **PubMedBERT** to represent medical terminology and entities extracted from the associated clinical text.

This provides domain-specific semantic information that complements the visual features.

#### 3. Transformer Decoder

A **Transformer-based decoder** generates the final caption autoregressively.

The decoder uses information from both the visual representation and medical entity features to produce a context-aware description.

#### 4. Explainable AI

The system provides visual interpretability through attention-based analysis and region-of-interest visualization, helping identify image regions associated with the generated caption.

---

## 🔄 How the System Works

### Step 1 — Medical Image Input

The system accepts medical images from different imaging modalities, including:

- X-Ray
- CT
- MRI
- Ultrasound
- PET

<img width="837" height="767" alt="Dataset" src="https://github.com/user-attachments/assets/09a10280-5ba8-4b00-82b1-099254b0e38e" />

### Step 2 — Image Feature Extraction

The input image is processed using **DenseNet-121** to obtain meaningful visual feature representations.

### Step 3 — Medical Entity Processing

Relevant entities are extracted from the associated clinical text using NLP processing techniques.

The entities are processed using **PubMedBERT** to obtain contextual medical representations.

### Step 4 — Multimodal Feature Fusion

Visual features from the CNN and semantic information from the medical entities are combined before being provided to the Transformer decoder.

### Step 5 — Caption Generation

The Transformer decoder generates a caption describing the medical image while incorporating relevant clinical entities.

### Step 6 — Explainability

Attention-based visualizations and ROI analysis are used to show which areas of the image contribute to the generated description.

---

## 🗂️ Dataset

The project uses the **ROCO (Radiology Objects in COntext)** dataset.

The dataset contains medical images paired with captions and associated radiological information.

### Dataset Modalities

The dataset includes multiple types of medical imaging, such as:

- CT
- MRI
- X-Ray
- Ultrasound
- PET

The dataset is used for training, validation, and testing of the medical image captioning system.

---

##  Data Processing

The dataset is processed before training to prepare both the image and textual information.

The preprocessing pipeline includes:

- Image cleaning and resizing
- Caption preprocessing
- Medical entity extraction
- Tokenization
- Removal of unsuitable or incomplete samples
- Preparation of image-text pairs
- Train, validation, and test splitting

After preprocessing, the dataset contains:

```text
Training   : 59,958 images
Validation : 9,876 images
Testing    : 9,905 images
```

---



### Training Configuration - using PyTorch

```text
Model              : DenseNet-121 + Transformer
Language Model     : PubMedBERT
Framework          : PyTorch
GPU                : NVIDIA Tesla T4
Training Platform  : Google Colab Pro
Training Epochs    : 60
Weight Decay       : 0.01
```

The training process uses cross-entropy loss for optimizing the caption generation objective.

---

## 🔍 Explainable AI

An important component of the project is visual interpretability.

The system provides attention-based visualizations to help understand the relationship between the generated caption and image regions.

The visualization pipeline includes:

- Attention maps
- Region-of-interest (ROI) visualization
- Image feature analysis
- Entity-focused visual interpretation

These visualizations provide additional insight into the model's caption generation process.

---

## 🛠️ Technology Stack

### Deep Learning

- Python
- PyTorch
- TorchVision
- DenseNet-121
- Transformer

### Natural Language Processing

- PubMedBERT
- SpaCy
- NLTK
- Hugging Face Transformers

### Computer Vision

- OpenCV
- Pillow

### Data Processing

- NumPy
- Pandas

### Visualization

- Matplotlib
- Seaborn

### Development Environment

- Google Colab Pro
- NVIDIA Tesla T4 GPU
- Jupyter Notebook

---


## 🚀 How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/entity-aware-medical-image-captioning.git
cd entity-aware-medical-image-captioning
```

Replace `YOUR_USERNAME` with the GitHub username that owns the repository.

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Prepare the Dataset

Download and prepare the **ROCO dataset** according to the required directory structure.

Update the dataset paths in the notebook before running the training or inference pipeline.

### 4. Open the Notebook

Launch the Jupyter notebook:

```text
notebooks/Entity-Aware_Medical_Image_Captioning.ipynb
```

The notebook can also be executed in **Google Colab** with an appropriate GPU runtime.


## 📊 Results and Outputs

The `outputs/` directory contains selected visual results produced by the project.


