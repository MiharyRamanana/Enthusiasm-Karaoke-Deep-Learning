# Enthusiasm-Karaoke-Deep-Learning
This project was made during my semester abroad in Akinori Ito's lab at Tohoku University.

---

## Table of Contents

1. [Overview](#overview)
2. [Background](#background)
3. [Experiment Details](#experiment)
4. [Results](#results)


---

## Overview
This project aims to evaluate enthusiasm when singing karaoke using deep learning. A previous work from this lab used machine learning.

## Background
Karaoke machines can evaluate singing skill. However, it only considers the pitch accuracy of the singer. Singing enthusiasm evaluation refers to the process of identifying and measuring the level of enthusiasm or passion in a person's singing performance. Emotion recognition through deep learning is an important area of research, playing a crucial role in the human computer interaction domain. The emotions commonly studied are sad, happy, angry, calm, fearful, neutral, disgust, sadness, fear/anxiety, boredom, excited, frustrated, and surprised. In this research, we use deep learning to evaluate enthusiasm.

## Experiment Details
We use the audio dataset from the Ito-Nose Lab of the Graduate School of Engineering of Tohoku University. The dataset contains 480 samples between 1 and 9 seconds, which are 240 stimuli sung with enthusiasm then without.
We initially have a dataset of size 480, which is low. So we want to increase this size to help us generalize our model. Audiomentations is a library for audio data augmentation. We preprocess the data using audio transformations such as AddGaussianNoise, TimeStretch, PitchShift, Shift, Gain and PolarityInversion. We manage to get a dataset of size 3840
The length of each audio file is adjusted to the length of the longest audio file of the dataset.
We then extract the Mel-scaled spectrogram of the samples. Mel-scaled spectrograms are commonly used to identify and track the timbre fluctuations of a sound file.

![image](https://github.com/user-attachments/assets/e76739e3-8b03-4ed2-abd0-44dc2c78e6dd)


60% of the dataset was used as training while 20% for validation and 20% for testing.
We then normalize the three sets.
The strategy is to use Computer Vision and Supervised Learning and let the deep neural network to find the features to determine whether the spectrogram corresponds to an enthusiastic audio or not.
We use a 4-layers convolutional neural network (CNN) based on the Mel-scaled spectrogram. Our model includes two dimensional convolution layers with batch normalization, activation layers and dropout. The input data received by the first layer of our CNN is an array of shape of (128, 216, 1). 
Our model uses Adam optimizer with a learning rate of 10-3. The metrics we used is Mean Squared Error.
We use early stopping to avoid training for too long.

## Results
In the paper, the Pearson correlation coefficient was 0.62 for linear regression. We manage to have a Pearson correlation coefficient of 0.90 with our CNN model.

![image](https://github.com/user-attachments/assets/5da02bcb-d0ba-4c30-b3aa-e7f592295b89)

However, when we try to generalize the model by using only the Elly dataset to train and the Favorite songs dataset to test, we obtain a Pearson correlationcoefficient of 0.45, which is too low.





