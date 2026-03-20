# 🧠 Brain Tumor Detection and Segmentation using Deep Learning

## 📌 Overview
This project presents a deep learning-based pipeline for **automated brain tumor detection and segmentation** from MRI scans. The system follows a **two-stage approach**:

1. **Classification (Tumor / No Tumor)** using ResNet50  
2. **Segmentation (Tumor Localization)** using ResUNet  

The models achieve:
- ✅ **97.57% Classification Accuracy**
- ✅ **0.89 Dice Coefficient for Segmentation**

This pipeline can assist medical professionals in **early diagnosis and treatment planning**.

---

## 🎯 Problem Statement
The task is divided into two sub-problems:

- **Binary Classification**  
  Detect whether a brain MRI contains a tumor.

- **Semantic Segmentation**  
  Identify and outline the exact tumor region at the pixel level.

---

## 📊 Dataset
- **Source**: LGG MRI Segmentation Dataset (Kaggle)
- **Total Samples**: 3929 MRI scans

| Class        | Samples |
|-------------|--------|
| No Tumor     | 2556   |
| Tumor        | 1373   |

⚠️ The dataset is **imbalanced**, which influences model training.

Each sample contains:
- MRI Image  
- Corresponding Segmentation Mask  
- Binary Label (0 / 1)

---

## 🧠 Model Architecture

### 🔹 1. Tumor Classification (ResNet50)

- **Backbone**: Pretrained ResNet50 (ImageNet)
- **Strategy**: Transfer Learning (Frozen base layers)

#### Custom Head:
- AveragePooling2D
- Flatten
- Dense (256, ReLU) + Dropout (0.3)
- Dense (256, ReLU) + Dropout (0.3)
- Output Layer (Softmax, 2 classes)

📌 Purpose:
Efficient feature extraction + fast convergence

---

### 🔹 2. Tumor Segmentation (ResUNet)

A hybrid architecture combining:
- **ResNet-style residual blocks**
- **U-Net encoder-decoder structure**

#### Key Components:
- Encoder → Feature extraction + downsampling  
- Bottleneck → Deep feature representation  
- Decoder → Upsampling + skip connections  
- Output → Sigmoid activation (binary mask)

#### Highlights:
- Residual connections improve gradient flow  
- Skip connections preserve spatial details  
- Designed for **pixel-level precision**

---

## ⚙️ Training Setup

### 🔹 Classification Model
- Loss: `categorical_crossentropy`
- Optimizer: Adam
- Metric: Accuracy
- Image Size: 256 × 256
- Batch Size: 16
- Data Augmentation: Normalization (1/255)

---

### 🔹 Segmentation Model
- Loss: **Focal Tversky Loss**
- Optimizer: Adam (LR = 0.05)
- Metric: Tversky Index

📌 Why Focal Tversky?
- Handles **class imbalance**
- Focuses on difficult tumor regions

---

## 📈 Results

### 🔹 Classification Performance

| Metric        | No Tumor | Tumor |
|--------------|---------|-------|
| Precision     | 0.98    | 0.98  |
| Recall        | 0.99    | 0.96  |
| F1-score      | 0.98    | 0.97  |

✅ Strong performance across all metrics  
✅ Low false positives and false negatives  

---

### 🔹 Segmentation Performance

- **Dice Coefficient**: **0.89**

📌 Interpretation:
- High overlap between predicted and true tumor regions  
- Accurate boundary detection  

---

## 🔍 Key Insights

- Transfer learning with ResNet50 significantly improves classification performance  
- ResUNet effectively captures both **global context and fine details**  
- Focal Tversky Loss helps overcome class imbalance in segmentation  
- Two-stage pipeline improves reliability compared to single-model approaches  

---

## 🚀 Applications

- Clinical decision support systems  
- Automated radiology workflows  
- Early tumor detection  
- Treatment planning and monitoring  

---

## ⚠️ Limitations

- Dataset imbalance may affect generalization  
- Limited to LGG tumor type  
- Real-world deployment requires multi-modal MRI validation  

---

## 🔮 Future Work

- Extend to multi-class tumor classification  
- Use 3D CNNs for volumetric segmentation  
- Deploy as a real-time web/clinical tool  
- Integrate explainability (Grad-CAM)

---

## 📚 References

- ResNet Paper: Deep Residual Learning for Image Recognition  
- Transfer Learning Resources  
- Focal Tversky Loss Implementation  
- CNN Visualization Tools  

---

## 🏁 Conclusion

This project demonstrates a robust deep learning pipeline for brain tumor detection and segmentation.  

- **ResNet50** delivers highly accurate tumor detection  
- **ResUNet** provides precise tumor localization  

Together, they form a powerful system capable of assisting medical professionals and improving diagnostic workflows.

---
- **Accuracy**: 97.57%
