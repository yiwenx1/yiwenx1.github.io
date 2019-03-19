---
title: ML Interview Review
description: Review of machine learning frequently asked questions.
categories:
- Machine Learning
tags:
- interview
---
# ML Interview Review

## Basic Machine Learning
### Activation functions
The range of sigmoid function is [0,1]. The Tanh activation function is a shifted version of sigmoid function, and its range is [-1, 1]. Usually tanh works better than sigmoid for hidden units because the mean of its output is closer to zero, so it centers the data better for the next layer. The disadvantage of these functions is that if the input is too small or too high, the slope will be near zero which will cause gradient descent problem.

In order to solve slow gradient descent problem, we use RELU function. $RELU = max(0,z)$. $Leaky\_RELU=max(0.01z,z)$. So if z is negative, the slope in RELU is 0, in Leaky_RELU is 0.01.

Why we need non-linear activation functions? If we only use linear activation function, the output will always be linear like logistic regression whatever hidden layers you add. So it is useless in complex problems.

### Random Initialization
In logistic regression we can initialize weights with zeros, however, in NN we need to initialize weights randomly (bias can be zeros). If we initialize all the weights with zeros, all hidden units will be completely identical (symmetric), and on each gradient descent iteration all the hidden units will always update the same. Therefore, we need to initialize weights with a small random number. Why small? Because if we use sigmoid or tanh, with large weights we may get a large Z at the very starting of training, it will slow down learning. If we use other activation function, then this is less of an issue.

### Parameters vs Hyperparameters
parameters: W and b.
hyperparameters: learning rate, number of iteration, number of hidden layers, number of hidden units, choice of activation functions.

### Bias and Variance
underfitting: high bias

overfitting: high variance

If model has high bias, 1. make NN bigger (size of hidden units, number of layers). 2. try different model. 3. run it longer. 4. optimization algorithms.

If model has high variance: 1. more data. 2. regularization. 3. try different model.

###  Regularization
L1 norm: $||W||_1=Sum(|w[i,j|)$ (sum of absolute values of all w)

L2 norm: $||W||_2 = \sqrt{Sum(|w[i,j]|^2)}$.

The normal cost function we want to minimize is $J(W, b) = \frac{1}{m}Sum(L(y^{(i)}, y^{'(i)}))$


### Gradient descent vs stochastic gradient descent.

update rule with one example: $\theta_j := \theta_j - \alpha\frac{\partial}{\partial\theta_j}J(\theta)$ For Least Mean Squares, we have that $\theta_j := \theta_j + \alpha(y^{(i)}-h_\theta(x^{(i)}))x_j^{(i)}$

GD: for every j, $\theta_j := \theta_j - \alpha\sum_{i=1}^{m}(y^{(i)}-h_\theta(x^{(i)}))x_j^{(i)}$. Gradient descent is susceptible to local minima. if m is large, ir runs slowly. 

SGD: for i = 1 to m: for every j: $\theta_j := \theta_j + \alpha(y^{(i)}-h_\theta(x^{(i)}))x_j^{(i)}$. Each time we encounter a training example, we update the parameters according to the gradient of the error with respect to that single training example only. SGD reaches convergence much faster since it updates wight more frequently. In order to obtain accurate results with SGD, the data sample should be in a random order, so we need to shuffle the training set for every epoch.

* optimizer
1. momentum: is used to accelerate SGD by navigating along the relevant direction and softening the oscillations in irrelevant directions.
$\gamma$ is u

## System Design Problem
* machine learning model design

1. Core problem: what is the goal of this problem? Formulate the problem and determine whether this is a regression or classification problem. What is the output? It is multi-class? Do we need multi-stage models?
2. Data. How many data we can collect and how? Do we need to do further process of the data? Is data biased? sparsity?
3. Features. Distinguish the features into different domains. What features we are going to extract from each domain? Is it sparse feature or dense feature? How do you scale features? Is it a category or continuous value?
4. Model. If it is a common problem, then propose different machine learning models and compare them in different scope. e.g., why use NN instead of DT? Why ensemble methods? If the problem is complicated, it would be nice to have a multi-stage model.
5. Evaluation. What metrics? How do you split train and test data? Do you do cross validation? Do you use entropy or PR curve or RoC curve to evaluate the model?
6. Optimization. After the initial model is evaluated, how to improve the model? Can you come up with more features to help the improvement? e.g., if the problem is a recommender system, then consider cold start problem.