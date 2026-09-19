---
title: "Understanding the Perceptron: The Building Block of Neural Networks"
date: 2026-09-19
categories: ["Neural Networks (General)"]
image: "/perceptron_diagram.png"
---

The **perceptron** is one of the simplest artificial neural network architectures. It acts as a fundamental building block for modern deep learning.

At its core, a perceptron takes multiple binary or real-valued inputs, combines them using weights and a bias, and passes the result through an activation function to produce a single output.

![Perceptron Diagram](/perceptron_diagram.png)


## How a Perceptron Works

A single perceptron processes information in two main steps: **linear summation** and **activation**.

### 1. Weighted Summation ($z$)

The input values ($x_1, x_2$) are multiplied by their respective weights ($w_1, w_2$). Weights represent the relative importance of each input signal. A constant value called the **bias** ($b$) is added to shift the decision threshold.

The total input $z$ is computed as:

$$
z = w_1 x_1 + w_2 x_2 + b
$$

In vector form, this is often written as $z = \mathbf{w}^T \mathbf{x} + b$.

### 2. Activation Function (Unit Step Function)

Once $z$ is calculated, it passes through an **activation function** to determine the final output $y$.

For a classic perceptron, we use a **Heaviside step function** (or unit step function):

![Unit Step Plot](/unit_step_plot.png)


$$
y = \begin{cases} 0, & \text{if } z < 0 \\ 1, & \text{if } z \ge 0 \end{cases}
$$

* **If** $z \ge 0$**:** The neuron "fires" and outputs **1**.
* **If** $z < 0$**:** The neuron stays inactive and outputs **0**.


## Geometric Intuition

The equation $w_1 x_1 + w_2 x_2 + b = 0$ defines a **decision boundary** (a line in 2D space, or a hyperplane in higher dimensions).

* Inputs on one side of the line yield $y = 1$.
* Inputs on the other side yield $y = 0$.

Because of this, a simple perceptron can only classify data that is **linearly separable** (like AND or OR logic gates). It cannot solve non-linear problems like the XOR function unless combined into multi-layer networks (MLPs).

---

## Python Code Example

Here is how you can implement a basic perceptron in Python:

```python
import numpy as np

def perceptron(x1, x2, w1, w2, b):
    # Step 1: Compute weighted sum z
    z = (w1 * x1) + (w2 * x2) + b
    
    # Step 2: Apply Unit Step Function
    y = 1 if z >= 0 else 0
    return y

# Example: OR Gate Logic
# Weights: 1.0, 1.0 | Bias: -0.5
print("0 OR 0 =", perceptron(0, 0, w1=1.0, w2=1.0, b=-0.5))  # Output: 0
print("1 OR 0 =", perceptron(1, 0, w1=1.0, w2=1.0, b=-0.5))  # Output: 1
print("0 OR 1 =", perceptron(0, 1, w1=1.0, w2=1.0, b=-0.5))  # Output: 1
print("1 OR 1 =", perceptron(1, 1, w1=1.0, w2=1.0, b=-0.5))  # Output: 1
```
