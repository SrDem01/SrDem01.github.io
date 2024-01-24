---
title: Kernel Regression
tags:
categories:
date: 2024-01-23
lastMod: 2024-01-23
---
# Resources

![MLClassLecture3.pdf](/assets/mlclasslecture3_1705974214063_0.pdf)

  + {{video https://www.youtube.com/watch?v=wBVSbVktLIY}}

# What is a kernel?

  + The linear algebra one.

  + So, the idea is that you can compute some dot product of the feature space with a function of the original vectors.

  + This function is called the kernel function.

    + $$k(x_i, x_j) = \phi(x_i)'\phi(x_j)$$

# In linear regression

  + Take a function of the data $\phi(X)$ as our feature vector.

  + For estimation, we usually use

    + $$\hat{\beta} = (X'X)^{-1}XY$$

  + If we had $\phi(X)$ as our feature vector instead,

    + $$\hat{\beta} = (\phi(X)'\phi(X))^{-1}\phi(X)Y$$

  + Apparently, it is really difficult to compute the $ bit.

    + This is also known as the covariance matrix.

  + With some simplification, we can rewrite the solution as

    + $$\phi(X)' (\phi(X) \phi(X)')^{-1}Y$$

  + The insides of the $\phi(X)\phi(X)'$ are all dot products.

  + But a kernel function compute this dot product using the $x_i$ directly.

    + Which is much faster, I suppose.

    + The matrix just needs to be symmetric and positive semi-definite.

      + Mercer's theorem

    + Which it is for the polynomial regression.

  + Rewriting with the kernel matrix, $K$

    + $$\hat{\beta}=\phi(X)' K^{-1}Y$$

  + We still need $\phi$ for weights

  + But if we want to make predictions we need $\hat{y} = \hat{\beta}'\phi(x)$.

  + Plugging in the value of the $\hat{\beta}$,

    + $$\hat{y} = Y K^{-1}\phi(X)' \phi(x)$$

  + The term $\phi(X)'\phi(x)$ is another vector of dot products

  + This can be replaced with a vector of kernel functions.

    + $$\hat{y} = Y K^{-1}k_x$$

  + The fundamental point is that you do not need $\phi$ to predict at all.

  + So, you can just start with a kernel only directly

  + It will implicitly define a feature space on its own.

# Common Kernels

  + Linear

  + Polynomial

  + Gaussian
