# Face Recognition using CNN on LFW Dataset

## Project Overview
This project implements a custom Convolutional Neural Network (CNN) using PyTorch to perform facial recognition. It is trained on the Labeled Faces in the Wild (LFW) dataset, which contains thousands of images of faces collected from the internet, designed for studying unconstrained face recognition.

## Dataset
* **Source:** [Kaggle - LFW Dataset](https://www.kaggle.com/datasets/jessicali9530/lfw-dataset)
* **Structure:** Deep-funneled images organized in folders by identity.
* **Preprocessing:** Images are resized to 128x128 pixels, converted to tensors, and normalized.

## Environment
This project is built for execution in **Google Colab**, utilizing its GPU acceleration for efficient deep learning training.

## Prerequisites
* A valid Kaggle account.
* A Kaggle API token (`kaggle.json`) uploaded to the Colab environment.

## Project Structure
1. **Kaggle Setup:** Automates the downloading and extraction of the LFW dataset directly from Kaggle into the Colab filesystem.
2. **Setup and Imports:** Configures PyTorch and detects hardware accelerators.
3. **Data Loading:** Uses `torchvision.datasets.ImageFolder` to dynamically load and label the image directory, applying transformations, and splitting the data into an 80/20 train/test split.
4. **CNN Architecture:** Implements `FaceCNN` with three convolutional layers (each followed by ReLU and Max Pooling) and fully connected layers with Dropout for regularization.
5. **Loss & Optimizer:** Uses Cross-Entropy Loss and the Adam optimizer.
6. **Training Loop:** Trains the model over 10 epochs, computing loss and updating network weights.
7. **Evaluation:** Tests the trained network on the 20% validation split and outputs the final classification accuracy.

## Usage
1. Open a new notebook in Google Colab.
2. Set the runtime to **GPU** (Runtime > Change runtime type > Hardware accelerator > T4 GPU).
3. Paste each chunk of code into sequential cells.
4. Run all cells in order.