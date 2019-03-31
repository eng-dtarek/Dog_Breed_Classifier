# Dog Identification Application

This project aims to develop an algorithm that could be used as part of a mobile or web app that will accept any user-supplied image as input. If a dog is detected in the image, it will provide an estimate of the dog's breed. If a human is detected, it will provide an estimate of the dog breed that is most resembling.

## Datasets

Two datasets are used in this project

- [dog dataset](https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/dogImages.zip).
- [human dataset](https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/lfw.zip).

## Detect Human Faces

In this section, OpenCV's implementation of [Haar feature-based cascade classifiers](https://docs.opencv.org/trunk/d7/d8b/tutorial_py_face_detection.html) is used to detect human faces in images.

After applying human faces detection function on both human and dogs datasets we got the following performance.

- The percentage of human images detected by face detector. 98.0.
- the percentage of dog images detected by face detector. 17.0.

## Detect Dogs

In this section, VGG-16 model is used to detect dogs in images.

After applying human dogs detection function on both human and dogs datasets we got the following performance.

- The percentage of human images detected by VGG16 dog detector. 0.0.
- The percentage of dog images detected by VGG16 dog detector. 96.0.

## Create a CNN to Classify Dog Breeds (from Scratch)

Now that we have functions for detecting humans and dogs in images, we need a way to predict breed from images. In this step, a CNN is implemented that classifies dog breeds.

Some Data Augmentation are applied on the dataset like resizing, random crop, flips, rotations and normalization.

**Model Architecture**

I started by searching for the best convolutional neural network structures that are used to classify dogs breeds images. for simple network, from 3 to 6 convolutional layers are used with fully connected layers along with Relu activation function, Max pooling and dropout. I began with 3 convolution layer and 2 fully connected layers. which resulted in poor results. I thought that may be the number of convolutional layers were not enough to capture more details. So I increased the number of convolutional layers to 5 instead of 3 which increased the accuracy but I thought that better results could be achieved. I noticed that some structures use only one fully connected I thought of trying it with doubt of any increase but but I was surprised by the accuracy increase which was an indicator that the simpler structures are always better.

**Loss Function and Optimizer**

CrossEntropy is used as loss function along with SGD optimizer.

**Performance**

After 30 epochs of training the model got 3.5 test loss and 22% test accuracy.

## Create a CNN to Classify Dog Breeds (using Transfer Learning)

First step was to choose CNN architecture that was used in a similar problem and acheived good results. I know that our problem is very similar to imagenet problem. Both are image classification problems with RGB images. So I decided to use one of the well known models used in imagenet to extract the image features then update the classifier to match the target output. I started with VGG16 due its high performance on imagenet problem along with its simplicity. I changed the last layer of the classifier to have 133 output features instead of 1000 to match the number of dog breeds. The accuracy was better than the minimum requirement. So I was satisfied with it and didn't try anything else due to the limited resources.

**Loss Function and Optimizer**

CrossEntropy is used as loss function along with SGD optimizer.

**Performance**

After 30 epochs of training the model got 0.55 test loss and 83% test accuracy.

## Algorithm Implementation

An algorithm is implemented that accepts a file path to an image and first determines whether the image contains a human, dog, or neither. Then,

1. If a dog is detected in the image, return the predicted breed.
2. If a human is detected in the image, return the resembling dog breed.
3. If neither is detected in the image, provide output that indicates an error.

## Algorithm Testing

Six images are used to test the algorithms. Two hyman images, two dogs images, and two babies images.

For dog images, the algorithm detect them as dog images with perfect breed classification. The human images also are detected as human face with resembling dog breed. but for me it's not clear how to measure the accuracy of it. Regarding images of babies, the algorithm can't detect them as human or dogs which is expected because the dataset doesn't include babies images.

**Possible points for improvement**

- Adding images of different aged humans to be able to detect all human faces regardless of the age.
- Fine tuning the parameter of the transfer_model with more training to get better accuracy.
- Searching for a way to measure the accuracy of the resembling dog breed of the human faces images.
