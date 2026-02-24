---
layout: post
title: "An Introduction to Neural Networks with MNIST"
date: 2026-02-24
---

# How a Neural Network "Sees" a Digit 🧠🔢

![Neural Network Architecture](_posts/mnist.png)

This diagram illustrates a **Feedforward Neural Network** (specifically a Multi-Layer Perceptron) performing one of the most famous tasks in AI: recognizing handwritten digits.

---

### 1. The Input: Image Flattening
Computers don't see "shapes" initially; they see a grid of numbers. 
* **The Image:** A $28 \times 28$ pixel grayscale image.
* **The Process:** To make the math work, we "flatten" the grid into a single **784-length vector** ($28 \times 28 = 784$).
* **The Data:** Each box in that column represents the brightness of one specific pixel.

### 2. The Hidden Layer: Feature Detection
The middle layer consists of **128 neurons**. This is the "engine room" of the network.
* **Weights (The Colored Lines):** Every pixel is connected to every neuron. The lines represent "Weights"—the network's way of deciding which pixels are important for which digit.
* **ReLU Activation:** The "L-shape" symbol inside the circles represents **ReLU** ($f(x) = \max(0, x)$). It acts as a gate, allowing only the most important signals to pass through.



### 3. The Output Layer: The Final Verdict
The final layer has **10 neurons**, representing the possibilities: **0 through 9**.
* **Sigmoid/Softmax:** The "S-curve" symbol represents a mathematical function that squashes the incoming signals into a **probability** between 0 and 1.
* **The Prediction:** In the example above, the neuron for **"3"** would have the highest value (e.g., 0.98), telling us the AI is 98% sure it sees a three.



---

### Why is this important?
While modern AI uses more complex "Convolutional" layers to keep track of spatial patterns, this architecture is the foundation of all deep learning. It shows how we turn raw data into a logical decision using nothing but math and layers!
