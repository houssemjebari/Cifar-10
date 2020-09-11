# Cifar-10

This Project builds an end-to-end computer vision multi-class Image Classifier using TensorFlow with the **Cifar 10** Dataset;

## What is Cifar-10 Dataset ?
The Cifar-10 is a labeled subset of the 80 million tiny images dataset. They were collected by Alex Krizhevsky, Vinod Nair, and Geoffrey Hinton. This data is from the official website of Toronto University : https://www.cs.toronto.edu/~kriz/cifar-10-python.tar.gz
The dataset contains 60,000 32x32 color images in 10 different classes. The 10 different classes represent airplanes, cars, birds, cats, deer, dogs, frogs, horses, ships, and trucks. There are 6,000 images of each class

## Why Cifar-10 ?
The CIFAR-10 dataset (Canadian Institute For Advanced Research) is a collection of images that are commonly used to train machine learning and computer vision algorithms. It is one of the most widely used datasets for machine learning research and as  a matter of fact, this dataset is perfect for my first Computer Vision Project

## Workflow 
This project workflow is classic and doesn't stand out from the rule  of usual Data Science Projects workflows:
* Download the Data 
* Preprocess the Data
* Modeling 
* Evaluating and predicting;

In this Part I'm only going to describe The data pipeline, the hardware used  and the model

### Data Pipeline 
In this Project I used the TensorFlow data API to build the pipeline which consists of:
* **mapping** : we map a function if needed to get Data-Augmentation
* **shuffling** : we shuffle the data to make sure there are no model inconsistencies
* **batching** : we batch the data after shuffling it with a batch size corresponding to the hardware we are using
* **caching** : caching is possible in the case of this dataset since it is not voluminous (<250MB)
* **prefetching** : prefetching is used to limit the I/O time overhead 

### Hardware : 
This project was built in colab So in this project i used both TPUs and GPUs depending on the hardware chosen some configurations will be changed automatically in this project :
* **GPU** : when using GPUs the batch size is set to 128 and and a mixed policy using 16 bit floating point is used which increases time performance. As a matter of fact, along with the previous pipeline we get a speed of 1s per epoch wich is 40 times faster than the basic CPU pipeline.
* **TPU** : when using TPUs the batch size is set to 1024 and we get a time performance of 1s per epoch also. Using mixed policy with TPUs is not supported yet since mixed policy is still experimental 

### Modeling : 
The model architecture I chose to use is VGG which is simple and perfect for this first Project and only requires using the Sequential Keras API.I achieved 85% accuracy working with this architecture and it can do better if further tuned. 
