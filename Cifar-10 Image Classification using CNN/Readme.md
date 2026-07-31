# CIFAR-10 Image Classification using CNN

## Project Overview
This project implements a Convolutional Neural Network (CNN) from scratch using PyTorch to classify images from the CIFAR-10 dataset. The model is designed to process $32 \times 32$ RGB images and output predictions across 10 distinct classes.

## Dataset
* **Source:** [CIFAR-10 Dataset](https://www.cs.toronto.edu/~kriz/cifar.html) (loaded directly via `torchvision.datasets`)
* **Size:** 60,000 $32 \times 32$ color images (50,000 training, 10,000 testing).
* **Classes:** Plane, Car, Bird, Cat, Deer, Dog, Frog, Horse, Ship, Truck.

## Environment
This code is optimized for execution within **Google Colab** using a hardware accelerator (GPU).

## Prerequisites
The following Python libraries are required (pre-installed in standard Colab environments):
* `torch`
* `torchvision`
* `matplotlib`
* `numpy`

## Project Structure
The notebook is divided into the following sequential execution blocks:
1. **Setup and Imports:** Initializes the environment and detects GPU availability (`cuda` or `cpu`).
2. **Data Loading and Preprocessing:** Downloads the CIFAR-10 dataset, applies tensor transformations, normalizes pixel values to a $[-1, 1]$ range, and initializes data loaders for batching.
3. **CNN Architecture Definition:** Defines a custom `SimpleCNN` class featuring:
   * 2 Convolutional Layers (`Conv2d`)
   * Max Pooling (`MaxPool2d`)
   * 3 Fully Connected Linear Layers (`Linear`)
   * ReLU Activation Functions
4. **Loss and Optimizer Configuration:** Utilizes Cross-Entropy Loss (`CrossEntropyLoss`) and Stochastic Gradient Descent (`SGD`) with momentum.
5. **Training Loop:** Trains the network over 10 epochs, iterating through batches, calculating gradients, and updating model weights.
6. **Model Evaluation:** Tests the trained network against the 10,000 unseen test images and calculates the overall prediction accuracy.

## Usage
1. Open a new Google Colab notebook.
2. Ensure the runtime type is set to **GPU** (Runtime > Change runtime type > T4 GPU).
3. Paste the code chunks sequentially into separate cells.
4. Run the cells from top to bottom.