Advanced Neural Network Framework (From Scratch)

A modular and configurable feedforward neural network implementation from scratch using NumPy, supporting multiple cost functions, L2 regularization, performance monitoring, and model serialization.

This project was built to deeply understand neural network internals without using high-level frameworks like TensorFlow or PyTorch.

Architecture

Example configuration:

net = network([784, 30, 10], cost=CrossEntropyCost)


Input Layer: 784 neurons (28×28 MNIST images)

Hidden Layer: 30 neurons

Output Layer: 10 neurons (digit classes 0–9)

The architecture supports arbitrary layer sizes.

Core Features
Modular Cost Functions

Quadratic Cost

Cross-Entropy Cost

Cost functions are implemented as independent classes and injected into the network during initialization.

Mini-Batch Stochastic Gradient Descent
net.sgd(
    training_data,
    epochs=30,
    mini_batch_size=10,
    eta=0.5,
    lmbda=5.0,
    evaluation_data=validation_data,
    monitor_evaluation_accuracy=True,
    monitor_evaluation_cost=True,
    monitor_training_accuracy=True,
    monitor_traning_cost=True
)


Supports:

Configurable epochs

Mini-batch training

Learning rate tuning

L2 regularization

Training and evaluation monitoring

L2 Regularization

Integrated directly into total cost computation to improve generalization:

𝜆
2
𝑛
∑
∣
∣
𝑊
∣
∣
2
2n
λ
	​

∑∣∣W∣∣
2
Backpropagation

Implements full gradient computation:

Forward propagation

Output layer error computation

Hidden layer error propagation

Weight and bias updates

Model Serialization

Save and load trained models using JSON:

net.save("model.json")
loaded_net = load("model.json")

Mathematical Overview

Forward pass:

𝑎
=
𝜎
(
𝑊
𝑎
+
𝑏
)
a=σ(Wa+b)

Output layer delta (Cross Entropy):

𝛿
=
𝑎
−
𝑦
δ=a−y

Hidden layer delta:

𝛿
𝑙
=
(
𝑊
𝑙
+
1
)
𝑇
𝛿
𝑙
+
1
⋅
𝜎
′
(
𝑧
𝑙
)
δ
l
=(W
l+1
)
T
δ
l+1
⋅σ
′
(z
l
)
Technologies Used

Python

NumPy

JSON (model serialization)

No external ML frameworks were used.

How to Run

Install dependencies:

pip install -r requirements.txt


Place mnist.pkl in the project directory.

Run:

python main.py

Key Improvements Over Basic ANN Version

Modular cost function abstraction

Cross-Entropy loss for improved gradient behavior

L2 regularization support

Training and evaluation performance monitoring

Model save/load functionality

Improved weight initialization options

Purpose

This project focuses on mastering:

Gradient flow mechanics

Optimization dynamics

Regularization techniques

Cost function behavior

Neural network modular design

It serves as a foundational implementation before moving to large-scale deep learning frameworks.