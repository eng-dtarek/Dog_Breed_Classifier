# Dog Identification Application

This project is a part of the [Deep Learning Nanodegree](https://www.udacity.com/course/deep-learning-nanodegree--nd101) at [Udacity](https://www.udacity.com/)

-- Project Status: Completed

## Project Introduction

Building a pipeline to process real-world, user-supplied images. Given an image of a dog, the algorithm will identify an estimate of the canine’s breed. If supplied an image of a human, the code will identify the resembling dog breed.

## Methods Used

- Deep Learning
- Convolutional Neural Networks
- Transfer Learning

## Technologies

- Python 3
- anaconda or miniconda
- PyTorch
- Numpy
- OpenCV
- tqdm
- PIL
- torchvision
- matplotlib
- jupyter notebook

## Project Description

The purpose of the project is to develop an algorithm that could be used as part of a mobile or web app that will accept any user-supplied image as input. If a dog is detected in the image, it will provide an estimate of the dog's breed. If a human is detected, it will provide an estimate of the dog breed that is most resembling.
OpenCV's implementation of Haar feature-based cascade classifiers is used to detect human faces in images. VGG-16 model is used to detect dogs in images.
I used Transfer Learning to create dog breed classifier that got 0.55 test loss and 83% test accuracy after 30 epochs of training. (for more details see this [documentation](https://github.com/eng-dtarek/Dog_Breed_Classifier/blob/master/report.html))

## Getting Started

1. Clone this repo (for help see this [tutorial](https://help.github.com/en/articles/cloning-a-repository)).
2. Install the above technologies
3. Create a new conda environment >> conda create --name deep-learning python=3
4. Enter the environment: (Mac/Linux) >> source activate deep-learning, (Windows) >> activate deep-learning
5. Run the following to open up the notebook server >> jupyter notebook
