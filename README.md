# Image-Classification-Simple-CNN-Using-Pytorch
This repository contains an implementation of a SimpleCNN architecture for classifying medical images from the OCTMNIST dataset. The project demonstrates a deep learning approach to image classification, specifically tailored for Optical Coherence Tomography (OCT) images.

### Dataset
The OCTMNIST dataset is part of the MedMNIST collection, which provides standardized medical image datasets. It contains grayscale images of Optical Coherence Tomography scans categorized into multiple classes. The dataset is widely used for research in medical imaging and machine learning.

For more information on the dataset, visit the MedMNIST repository.

### Model Architecture
The classification model is built using a Convolutional Neural Network (CNN) designed for simplicity and efficiency. The architecture is as follows:

##### First Convolutional Layer:
Input: Grayscale image with 1 channel.
Layer: Convolution with 32 output channels, 3×3 kernel, and padding of 1.
Activation: ReLU (Rectified Linear Unit).
Pooling: Max-pooling with a 2×2 kernel to reduce spatial dimensions.

##### Second Convolutional Layer:
Input: 32 feature maps from the previous layer.
Layer: Convolution with 64 output channels, 3×3 kernel, and padding of 1.
Activation: ReLU.
Pooling: Max-pooling with a 2×2 kernel to further reduce spatial dimensions.

##### Flattening:
The output from the second convolutional layer is flattened into a 1D vector for input into fully connected layers. After pooling, the feature map size is 
7×7, resulting in 64×7×7=3136 features.

##### First Fully Connected Layer:
Input: 3136 features.
Layer: Fully connected layer with 128 output features.
Activation: ReLU.

##### Second Fully Connected Layer:
Input: 128 features.
Layer: Fully connected layer with 4 output features corresponding to the number of classes in the OCTMNIST dataset.

### Summary of Layers

| Layer Type | Input Shape | Output Shape | Parameters |
|------------------|------------------|------------------|------------------|
| Convo2D (32 channels) | 1x28x28 | 32x28x28 | 32x(1x3x3+1) = 320|
| MaxPool2D | 32x28x28 | 32x14x14 | 0 |
| Convo2D (64 channels) | 32x14x14 | 64x14x14 | 64x(32x3x3+1) = 18496 |
| MaxPool2D | 64x14x14 | 64x7x7 | 0 |
| Fully Connected (128) | 3136 | 128 | 3136x128+128 = 401536 |
| Fully Connected (4) | 128 | 4 | 128x4+4 = 516 |

### Total Trainable Parameters
The total number of parameters in the model is 420,868.

### Project Highlights
This project showcases the following key features and capabilities:
##### Data Preprocessing:
The OCTMNIST dataset is preprocessed using normalization to scale pixel intensities to a [0, 1] range.
Data augmentation techniques (such as flipping and rotation) are optionally applied to enhance generalization.
##### Custom SimpleCNN Model:
A lightweight CNN architecture designed to efficiently classify grayscale OCT images.
Includes ReLU activations, max-pooling layers for dimensionality reduction, and fully connected layers for classification.
##### Efficient Training and Evaluation:
Supports training with adjustable hyperparameters such as learning rate, batch size, and number of epochs.
Evaluates model performance using standard metrics like accuracy and confusion matrix.
##### Visualization Tools:
Provides insightful visualizations of training and validation loss and accuracy curves to monitor model performance.
Includes confusion matrices and classification reports for detailed evaluation.
##### Reproducibility:
The code is modular and organized for easy replication of experiments.
Preprocessing, training, and evaluation are well-documented and easy to customize.
##### Applications:
Demonstrates potential for real-world medical imaging applications, highlighting the role of CNNs in healthcare technology.

### Requirements

Python 3.x
PyTorch
torchvision
matplotlib
numpy
scikit-learn
MedMNIST package (for dataset handling)

### Install the dependencies using:
