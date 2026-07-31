# Cancer Detection using MRI Images

## Project Overview
This project develops a Convolutional Neural Network (CNN) in PyTorch to detect cancerous tumors from Brain MRI scan images. The target task is binary classification, determining whether an MRI image indicates the presence or absence of a brain tumor.

## Dataset
* **Source:** [Kaggle - Brain MRI Images for Brain Tumor Detection](https://www.kaggle.com/datasets/navoneel/brain-mri-images-for-brain-tumor-detection)
* **Classes:** * `yes` (Tumor Detected)
  * `no` (No Tumor Detected)
* **Preprocessing:** Images are resized to $128 \times 128$ pixels, converted to PyTorch tensors, and normalized.

## Environment
This project is structured for execution in **Google Colab** with GPU acceleration enabled.

## Prerequisites
* Active Kaggle account.
* API Token file (`kaggle.json`) uploaded during execution.

## Workflow Pipeline
1. **Kaggle API Integration:** Securely downloads and unzips the dataset directly into the Google Colab environment.
2. **Environment Configuration:** Initializes PyTorch and binds computation to the available GPU (`cuda`).
3. **Data Preprocessing & Splitting:** Applies transformations to resize and normalize input images. Splits dataset into an 80/20 train/test split via `torch.utils.data.DataLoader`.
4. **CNN Architecture:** Builds a feature extraction backbone (3 Convolutional blocks with ReLU and Max Pooling) paired with a classification head using Dropout to reduce overfitting.
5. **Optimization:** Uses Cross-Entropy Loss alongside the Adam optimizer.
6. **Training Loop:** Trains the model over 15 epochs while logging batch losses.
7. **Evaluation:** Evaluates model generalization on the unseen test set and outputs overall accuracy.

## Execution Instructions
1. Create a new Google Colab notebook.
2. Set Runtime hardware accelerator to **GPU**.
3. Run the code cells sequentially from top to bottom.