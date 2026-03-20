# 🧠 Brain Tumor Segmentation using Deep Learning

## 🧠 Overview

This project presents a deep learning-based approach for brain tumor segmentation using MRI scans. The model performs pixel-wise prediction, identifying tumor regions within the brain rather than simply classifying presence or absence.

---

## 🎯 Objective

The goal is to:
- Segment tumor regions from MRI scans  
- Learn spatial patterns of tumors  
- Generate interpretable visual outputs  

---

## 🏗️ Problem Formulation

Binary image segmentation:

| Class | Meaning |
|------|--------|
| 0 | Background |
| 1 | Tumor |

---

## 📊 Dataset

- Input: Brain MRI images  
- Target: Corresponding segmentation masks  

Each sample contains:
- MRI image  
- Ground truth mask  

---

## ⚙️ Methodology

### Data Preprocessing
- Resizing images  
- Normalization  
- Mask alignment  

### Model Architecture
- CNN-based encoder-decoder model  
- Encoder extracts features  
- Decoder reconstructs segmentation mask  

### Training
- Loss: Binary Crossentropy / Dice Loss  
- Optimizer: Adam  

### Pipeline
MRI Image → Preprocessing → Model → Predicted Mask  

---

## 📈 Results

### Quantitative (Add your values)

| Metric | Score |
|------|------|
| Dice Coefficient | XX |
| Accuracy | XX |

---

## 🖼️ Sample Outputs

![Sample 1](outputs/sample1.png)  
![Sample 2](outputs/sample2.png)  

### Visualization Explanation
Each sample shows:
- Original MRI  
- Ground Truth Mask  
- Predicted Mask  
- Overlay comparison  

---

## 📊 Training Visualization

![Training Curve](outputs/training_curve.png)

---

## 🔬 Observations

- Good tumor localization  
- Strong overlap with ground truth  
- Minor boundary errors  
- Small tumors harder to detect  

---

## 💡 Key Contributions

- Pixel-wise tumor segmentation  
- End-to-end deep learning pipeline  
- Visual interpretation using overlays  

---

## ⚠️ Limitations

- Depends on dataset quality  
- Boundary precision is limited  
- No 3D context (2D slices only)  

---

## 🚀 Future Work

- Use U-Net / advanced architectures  
- Apply data augmentation  
- Extend to 3D MRI  
- Improve boundary detection  

---

## 📁 Project Structure

Healthcare_AI/
├── Copy_of_Healthcare_AI.ipynb  
├── dataset/  
├── outputs/  

---

## ▶️ How to Run

1. Open notebook in Colab/Jupyter  
2. Load dataset  
3. Run all cells  
4. Train model  
5. View outputs  

---

## 📦 Requirements

pip install tensorflow keras opencv-python numpy matplotlib  

---

## ✍️ Author

Sai Sohan Sajja  
Machine Learning | Computer Vision | Medical AI  

---

## 🧠 Research Relevance

This project demonstrates deep learning for medical image segmentation, a key area in healthcare AI for automated tumor detection and localization.
