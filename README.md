# RockPaperScissors-Classification

In this project, we used rock-paper-scissors dataset (https://www.tensorflow.org/datasets/catalog/rock_paper_scissors) to classify the hand gestures into rock, paper, and scissors. Code is provided in RockPaperScissor.ipynb

## Dataset description  
The original dataset is split into two groups, train and test (We later use test as our validation dataset). The training dataset includes 2520 images, and the testing one includes 372 images. The image size is 300*300 with 3 channels. The number of labels is 3 which are rock, paper, and scissors. Code to explore the dataset is under the “Load and explore the dataset” section.

## Data preprocess and augmentation
All images are resized to 200 * 200 * 3 and are rescaled among 0 to 1. In order to avoid overfitting on dataset, we randomly flip (both horizontal and vertical), adjust contrast, zoom, and rotate the images in training dataset. Code is under the “data augmentation” section.

## Model design
Input shape is 200 * 200 * 3 and the output is the softmax value of 3 groups. The model is consist of 4 layers of Conv2D with some average pooling and 3 layers of connected neuron network at the bottom. Mask size is 3*3. Best validation accuracy achieved 0.90

![improved_performance](https://user-images.githubusercontent.com/72532191/163004863-419b541e-0552-42a0-8b7a-ab3571e1783a.png)

## Prediction on real images
Since the dataset is CGI-based, we want to test our model performance on the real hand gesture images. Below is some results. (0, 1, 2 stands for rock, paper, scissors respectively)

![prediciton](https://user-images.githubusercontent.com/72532191/163005636-6eb71551-4cdd-4b94-9266-19fdc42dddbf.png)

These real test images were taken with 3 different backgrounds which are white background, floor, and background with multiple unrelated objects. The wrong predictions happen in rock-paper classification and scissors-paper classification.
Reason for the misclassification might be the excess data augmentation on the training dataset. Zooming on the original dataset makes some unreasonable hand shape which cuases the unreasonable variety to train the model. Here are some examples.

Paper-rock

![image](https://user-images.githubusercontent.com/72532191/163006181-909a2314-cf97-4865-9d7f-38571812f7d4.png)

Paper-scissors

![image](https://user-images.githubusercontent.com/72532191/163006263-5237d34c-efa3-4bb0-ba68-8b20e09bb5f9.png)
