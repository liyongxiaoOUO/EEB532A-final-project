# EEB532A-final-project
# Unsupervised Anomaly Detection on MVTec 'Bottle' using PaDiM

## Project Overview
This project implements **PaDiM (Patch Distribution Modeling)** for unsupervised anomaly detection, specifically targeting the **'Bottle' category** from the MVTec AD dataset.

The goal is to detect various defects (such as broken glass or contamination) without training on any anomalous samples. The model learns the statistical distribution of "normal" bottles using a pre-trained ResNet-18 and identifies outliers using Mahalanobis distance.

**Key Highlights:**
* **Method:** PaDiM (ResNet-18 Backbone).
* **Dataset:** MVTec AD (Bottle).
* **Environment:** Google Colab (T4 GPU).
* **Training Time:** < 2 minutes (One-pass calculation).

## Performance Results

Our implementation demonstrates state-of-the-art performance, particularly in pixel-level localization.

| Metric | Score | Description |
| :--- | :--- | :--- |
| **Image-level AUROC** | **99.76%** | Near-perfect detection of defective bottles. |
| **Pixel-level AUROC** | **98.33%** | High precision in segmenting defect shapes. |
| **F1-Score** | **0.9764** | Excellent balance between precision and recall. |

**Qualitative Analysis:**
The model successfully generated accurate anomaly heatmaps. It correctly identified:
1.  **Broken Large:** Large fractures at the bottom of the bottle.
2.  **Contamination:** Subtle internal dirt while ignoring light reflections on the glass surface.

## Methodology
We utilized **PaDiM**, a patch-based statistical method that embeds images using a pre-trained CNN.

1.  **Embedding Extraction:** Extracts features from ResNet-18 layers 1, 2, and 3.
2.  **Statistical Modeling:** Calculates the mean and covariance for each patch position to learn "normality".
3.  **Anomaly Scoring:** Uses Mahalanobis distance to measure the deviation of test images from the learned distribution.

## Getting Started

The easiest way to run this code is via Google Colab.

1.  Open the `.ipynb` file in this repository.
2.  Click the "Open in Colab" button (if available) or upload the notebook to your Colab drive.
3.  Ensure you are connected to a GPU Runtime.
4.  Run all cells to download the dataset and execute the model.

## Dependencies
* Python 3.8+
* PyTorch
* Torchvision
* Scikit-learn
* Matplotlib
* (Optional) Anomalib

## References
* **PaDiM Paper:** Defard, T., et al. (2020). *PaDiM: a Patch Distribution Modeling Framework for Anomaly Detection and Localization*.
* **MVTec AD Dataset:** Bergmann, P., et al. (2019).

---
