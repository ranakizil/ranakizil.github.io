---
layout: post
title: "An Introduction to Neural Networks with MNIST"
date: 2026-02-24
math: true
---

### What is MNIST database?
MNSIT stands for **Modified National Institute of Standards and Technology**. It is a large collection of handwritten digits that has been the standard benchmark for training image processing systems since the late 1990s. Every image in the MNIST data set has exactly *28 x 28* pixels.

### Sample images from the dataset:

![](/mnist_samples.png)

---
Now we are going to see how can we create a neural network to identify the given handwritten digit.

![MNIST](/mnist.png)

### 1. The Input: Image Preprocessing
The process starts on the far left with a small, 28x28 pixel grayscale image of the digit "3". At this point, the neural network doesn’t actually "know" it’s looking at a number; it just sees a grid of tiny squares.

Each of these **784 pixels** (28x28 = 784) has a value based on how bright it is, ranging from 0 to 1. A 0 means the pixel is pure black (the background), while a 1 means it is pure white (the ink of the pen). If a pixel is somewhere in between, like 0.9, it is a light gray.

To help the network understand this, we use a step called **preprocessing**. In this case, we "flatten" the image. Imagine taking each row of the grid and laying them out in one long, straight line, starting from the top-left and ending at the bottom-right.

Because the very first pixels in the top corner are black, we put a 0 for the first two spots in our vector. As we reach the actual curves of the "3", we start seeing values like 0.5, 0.7, and 1. Since the very last pixel in the bottom-right corner is also black, the last value in our array is also 0. This resulting 784-length vector acts as the input layer and we feed it to the network.

### 2. The Hidden Layer: Feature Extraction
The middle section shows a column of circles with 128 neurons. This is the "Hidden Layer." Notice the web of lines. Every single one of the 784 input pixels is connected to every one of the 128 neurons. Each line represents a Weight (*w*), which determines how much influence a specific pixel has on a specific neuron. Each neuron calculates a weighted sum of all inputs plus a "bias" (*b*).

We calculate the weighted sum with ($z = \sum w_i x_i + b$). After that we send the result to the neuron and the neuron uses it's activation function to give the output.

**Activation Function**
The activation function is essentially the **decision-maker** of the neuron. Without it, a neural network is just a giant linear calculator—no matter how many layers you add, it could only ever solve simple, straight-line problems.

In the "Hidden Layer" we use the **ReLu (The Rectified Linear Unit)** activation function. 

**ReLu (The Rectified Linear Unit)**

![relu](/relu.png)


$$f(z) = \max(0, z)$$


The most popular choice today. If the input is negative, it turns it into 0 (the neuron stays silent). If it’s positive, it passes the value through exactly as it is. It’s fast and helps the network learn complex patterns.


### 3. The Output Layer: Making a Guess
