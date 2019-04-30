---
title: ML Basics Preparation for Twilio Onsite
description: 
categories:
- Twilio
tags:
- Machine Learning
---
# ML Basics Preparation for Twilio Onsite

## Activation function
1. What is activation function?

Activation function decides whether a neuron should be activated or not. A neuron would calculated weighted sum of an input data and add bias with it, the activation function decides whether it should be passed to the next layer or not.

2. Examples of ReLU, sigmoid, softmax

The output of sigmoid function has range [0,1], function is $A=\frac{1}{1+e^{-z}}$.

Tanh is the shifted version of sigmoid function, it has range [-1,1], function is $A = \frac{e^z - e^{-z}}{e^z + e^{-z}}$. It is better than sigmoid because the mean of its output is closer to zero, so it centers data better for the next layer.

Disadvantage of sigmoid and Tanh: it input is too small or too large, the slope of the activation function would be nearly zero, which may cause gradient descent problem where the updates are slow.

Therefore, we use ReLU to solve slow gradient descent problem. The function is $A = max(0, z)$. 1) It avoid gradient vanishing problem, 2) sparse activation, reduce overfitting, 3) calculation is faster. Disadvantage of ReLU: when input is less than zero, the gradient descent is zero, so parameters cannot be updated, which might lose some information from data.

Therefore, we use leaky ReLU, the function is $Leaky\_ReLU=max(0.01z, z)$.

How to choose? If the classification is between 0 and 1, choose sigmoid, otherwise, choose ReLU. If too many neurons die in the network, choose leaky ReLU.

Why use non-linear activation functions? Linear activation function will only output linear activations. No matter how many layers you add, the activation will always be linear, so it doesn't work for complex problems. However, using some linear function in a neural network is acceptable, since it can help reduce the parameters we need to calculate.

Softmax is usually used as the output layer in a neural network since it maps the non-normalized output of a network to a probability distribution over all classes. $\sigma(x_i)=\frac{e^{x_i}}{\sum_{j=1}^{k}e^{x_j}}$. 


## Overfitting
1. data augmentation
2. reduce the complexity of model, e.g., reduce the number of layers in a neural network, or reduce the number of neurons in a layer, reduce the height of a decision tree, or pruning.

what is pruning in decision tree? 1) pre-pruning: when building a decision tree, estimate if splitting a node can improve the performance of decision tree. e.g., have a height restriction to a decision tree; when the number of instances of one node is less than a threshold; when the information gain is less than a threshold. 2) post-pruning: After building the decision tree, cut some nodes with their subtree based on the performance on validation set, if cutting a subtree won't decrease the performance of the decision tree, then cut the root node of the subtree.

3. L1 regularization and L2 regularization

It can reduce generalization error (performance on inputs not previously seen) but not training error. Regularization adds a penalty on parameters.

L1 norm: $||W|| = \sum_{i=1}^{k}|w_i|$ which is the sum of absolute values of all w. L1 regularization would shrink some parameters to zero, therefore it can be seen as a way of feature selection.

L2 norm: $||W||^2 = \sum_{i=1}^{k}|w_i^2|$ which is sum of all w squared. L2 norm is computational efficient because it has a unique solution.

4. ensemble learning, e.g., dropout in neural network, random forest or GBDT in ensemble learning
5. early stopping

## Two major categories of models under supervised learning

### generative models
A generative model models the actual distribution of each class. It learns the joint probability distribution $P(x,y)$ and predicts the conditional probability with the help of Bayes rule.

Calculate $P(y|x)$ using Bayes rule and $P(x|y)$ and $P(y)$. It models class-conditional pdfs and prior probabilities.

examples: Naive Bayes; Bayesian networks, HMM

### discriminative models
A discriminative model models the decision boundary between the classes. It learns the conditional probability distribution $P(y|x)$ directly. It directly estimate posterior probabilities.

examples: logistic regression, SVM, neural network, knn

naive bayes is called naive is because its assumption of conditional independence, i.e., all input features are independent from one another.

### advantages and disadvantages
NB: converge quicker than discriminative models and need less training data. Even if the NB assumption doesn't hold, it usually still does a good job. However, it can't learn interactions between features.

Logistic regression: Lots of ways to regularize. It has a nice probability interpretation.

## Why CNN can be applied in CV and NLP?
CNN can extract high-level feature from low-level features.