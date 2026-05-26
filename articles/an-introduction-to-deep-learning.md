# An Introduction to Deep Learning

**By Divya Iyer**  
**Date: March 20, 2026**

---

## Overview

Deep learning is the engine behind most of the AI you use every day. This article gives you a clear map of what it is, why it exists, how it works, and what it can do. If you have some familiarity with Machine Learning basics, this is where things get a lot more interesting.

There is a class of problems where classical ML simply cannot keep up, and deep learning is what fills that gap. Future articles will go deep on each part.

Before we touch any math or diagrams, here are some everyday things powered by the exact technology this article is about.

Google Photos groups your pictures by face and place, WhatsApp predicts your next word, Google Translate works across 130+ languages in real time, Alexa and Siri turn speech into action, and ChatGPT holds a conversation. None of these were programmed with rules. Instead they all learned from millions of examples. That is the core idea of deep learning.

---

## Why Do We Need Deep Learning at All?

Imagine trying to teach a computer to recognise a car.

A traditional ML approach doesn't "see" a car the way humans do. Instead, it depends on predefined features that humans decide are important:

- Does the image contain round shapes like wheels?
- Are there straight edges forming doors and windows?
- Is there a metallic texture or a certain body shape?

The challenge is we must manually decide what matters, and that's where things start to break down.

---

## The Problem with Traditional Approaches

This older approach works well when the data is structured like bank transactions or spreadsheets. But with images, audio, and language, things become far more complex.

Here are some of the key challenges with traditional approaches:

### 1. Cannot Handle Real-World Complexity

Real-world data is layered and non-linear, with subtle patterns that humans struggle to define. Traditional methods treat it as a flat list of numbers, thereby missing its deeper structure.

### 2. Heavy Dependence on Manual Features

Heavy reliance on manual feature design means humans must decide what matters. In messy, unpredictable real-world data, these assumptions often fail and limit the model.

### 3. Repetitive and Hard to Scale

Every new problem requires feature design from scratch, making the process repetitive and shifting effort to input engineering, often resulting in systems that are time-consuming, fragile, and hard to scale.

---

## The Turning Point

In 2012, a breakthrough happened.

A team trained a neural network directly on raw pixel data and significantly reduced error rates. This moment is called the **AlexNet breakthrough**. It marked the shift towards a new way of solving complex problems.

---

## Enter Deep Learning!

Deep learning is a modern approach that uses neural networks trained on large amounts of data. Instead of relying on manually defined features, it learns directly from raw input. Much like the human brain processes sounds and images, these networks gradually build understanding.

This ability to automatically learn meaningful patterns is what makes deep learning so powerful.

- Give it images → it learns edges, shapes, and objects
- Give it text → it learns grammar, context, and meaning

This removes a huge amount of human effort and is the core reason deep learning works so well on complex, raw data like images, audio, and language.

### Important Caveat

One important caveat: deep learning is not always the right choice. On small structured datasets like loan approvals or customer churn tables, a simpler model often works better and trains much faster. Deep learning is most useful when data is large, raw, and high-dimensional.

Machine learning is still important. But deep learning is where most modern innovation is happening.

---

## How Does It Work? Neural Networks from the Ground Up

A neural network is loosely inspired by the human brain. It is a layered system of simple units called neurons, each performing a small calculation. Together, they can learn remarkably complex patterns.

---

## How a Neuron Works inside a Neural Network

Every neuron in the network does the same four steps:

1. **Take inputs** from the previous layer, or directly from the raw data
2. **Multiply each input by a weight**. The weight decides how important that input is
3. **Add a bias**. This is a small fixed number that adjusts the result
4. **Pass everything through an activation function**. This decides how strongly the neuron reacts

**Formula:** Z = (weight × input) + bias

Each neuron takes its inputs, scales them by how important they are, adds a small offset, and passes the result forward. Individually each neuron is very simple. But thousands of them working together across many layers can learn patterns that no human could write by hand.

---

## The Structure of an Artificial Neural Network

The "deep" in deep learning comes from the fact that it has multiple layers, typically three main types. A neural network consists of an **input layer**, **hidden layers**, and an **output layer**. The input layer receives the raw data. The hidden layers in the middle transform and process it step by step. The output layer produces the final answer. Data flows through the network like an assembly line, with each layer building on the work of the one before it.

The more hidden layers you add, the more the network can learn. Here is what those layers pick up when trained on handwritten digits:

- **Layer 1:** Learns basic edges like straight lines, curves, and pixel intensity changes
- **Layer 2:** Combines these edges into simple patterns like strokes, corners, and loops
- **Layer 3:** Forms digit parts such as vertical bars (1), curves (2, 3), or circles (0, 6, 9)
- **Layer 4 and beyond:** Combines these parts to recognize complete digits like 0–9

Nobody told the network to do this. It learned it from the data. That is the core idea of deep learning.

---

## Activation Functions: Why They Matter

If every neuron just performs a weighted sum, stacking multiple layers still behaves like a single linear transformation, meaning depth adds no real power. To unlock the true potential of neural networks, we introduce **activation functions** at each neuron, applied after the weighted sum. These functions add non-linearity, allowing the network to learn complex patterns instead of collapsing into a simple linear model.

### Common Activation Functions

- **Step:** Outputs 0 or 1
- **Sigmoid:** Outputs a smooth S-curve between 0 and 1
- **Tanh:** Outputs centered between -1 and 1, often better than sigmoid
- **ReLU:** Zero for negative values and linear for positive, fast and widely used
- **Leaky ReLU:** Allows small negative values, helping avoid dead neurons

### The Most Popular: ReLU

The most popular choice today is **ReLU (Rectified Linear Unit)**. It is simply this: if the input is negative, output zero. If it is positive, pass it through unchanged. This simple rule trains faster than older functions and fixed a big training problem called the vanishing gradient. Future articles will cover each activation function in detail.

---

## How Does a Network Learn?

Training a neural network repeats the same three steps over and over:

### 1. Forward Pass

The input data moves through all the layers and produces a prediction.

### 2. Loss Computation

Compare that prediction to the correct answer using a loss function. This gives a number showing how wrong the network was:
- For classification tasks: Cross-Entropy
- For regression tasks: Mean Squared Error

### 3. Backpropagation

The network works backwards through the layers. It calculates how much each weight was responsible for the error, then adjusts each weight slightly to reduce it.

Repeat this thousands of times across the training data and the weights slowly settle into values that produce good predictions. The tool that controls how those weights are updated is called the **optimizer**.

---

## Optimizers: Finding the Best Weights

Optimizers take the error signal from backpropagation and use it to update the weights. The goal is to reach the **global optimum**, the point where the error is at its lowest. Here are the main types:

- **Gradient Descent (and Variants):** Uses full data for accurate but slow updates; SGD uses single data points for faster but noisy updates; Mini-batch uses small batches to balance speed and stability.

- **Adam:** Adapts learning rates for each weight automatically, fast and widely used.

- **SGD with Momentum:** Speeds up SGD by using past gradients to smooth updates.

- **Adagrad:** Adjusts learning rates based on past updates, good for sparse data but can slow down.

- **RMSprop:** Prevents Adagrad slowdown by keeping learning rates stable during training.

---

## What Can a Neural Network Output?

The output layer of the network changes depending on the problem you are solving:

### Regression

**Regression:** One output neuron with no activation. The network outputs a plain number like a house price, a temperature, or a stock value.

### Classification

**Binary Classification:** One output neuron with a sigmoid activation. It gives a number between 0 and 1. You use it to answer yes or no questions: is this email spam, is this image a cat, is this transaction fraud?

**Multi-Class Classification:** One neuron per class, with a softmax activation. Softmax makes all the outputs add up to 1 so they can be read as probabilities. Used when you have many possible answers, like which animal is this (cat, dog, etc.) or what language is this text?

---

## Keeping the Network Healthy

Training can run into two common problems. The first is **overfitting**, where the network memorises the training data instead of learning general patterns. The second is **instability**, where the gradients become too large or too small during training. Here are the tools that fix both:

### Regularization: Preventing Overfitting

- **Dropout:** During each training step, some neurons are randomly switched off. This stops the network from relying too heavily on any one path and forces it to learn more general patterns.

- **L1 and L2 Regularization:** These add a penalty for large weights. This keeps the model from putting too much importance on any single feature.

### Normalization: Keeping Training Stable

- **Batch Normalization:** Normalizes layer outputs to stabilize and speed up training.

- **Layer Normalization:** Normalizes each data point individually, useful for models like Transformers.

- **Residual Connections:** Add shortcuts (y = x + f(x)) to help gradients flow and train deep networks effectively.

---

## One Analogy to Tie It All Together

Think about the difference between teaching a child and programming a robot.

With a robot, you write rules: a cat has pointy ears, whiskers, and fur. The robot follows those rules exactly. But the moment it sees a cat that doesn't match your rules, it fails.

With a child, you just show examples. You point at cats over and over. The child builds up a sense of what a cat is without you ever explaining the rules. That is how deep learning works. You feed it examples. It figures out the patterns on its own.

---

## What Comes Next in This Series

- **Neural Networks in depth:** A closer look at neurons, layers, and activation functions working together.

- **Backpropagation:** How the network calculates and propagates error to update every weight.

- **Optimizers:** A deep dive into SGD, Momentum, RMSprop, Adagrad, Adam, and when to use each.

- **Normalization and Regularization:** The techniques that keep training stable and prevent overfitting.

- **Weight Initialisation:** Why how you start the weights matters more than most people realise.

- **CNNs, RNNs, Transformers:** The specialised architectures, each built for a different type of data, coming later in the series once the fundamentals are covered.

---

*Article by Divya Iyer | The Data Whisperer | March 20, 2026*
