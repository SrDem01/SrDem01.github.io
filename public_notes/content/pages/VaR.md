---
title: VaR
tags:
categories:
date: 2024-01-23
lastMod: 2024-01-23
---
# Value at Risk

  + For a given $$p$$,

    + it is the worst case scenario, discounting the other worse cases whose total probability is p.

![image.png](/assets/image_1705695894433_0.png)

  + Basically, the quantile of the associated distributions of the return.

## Critisism

  + Does not tell you what is the extent of the loss in case of the bad thing happens.

  + Solution: Conditional VaR

    + Also, called Expected Shortfall.

    + The *conditional* comes from conditioning on the VaR breach.

    + The expected value of the returns given a [VaR]({{< ref "/pages/VaR" >}}) breach, where X is the returns

      + $$E [X | X < VaR]=\int^{VaR} x f(x | x < VaR) dx$$

    + How to calculate bhaiii.

# Computation

  + Assume normality, and then do qnorm xD.

  + Fancy porfolio theory, baby.

  + VaR can be estimated either parametrically or nonparametrically.

  + [Quantile regression]({{< ref "/pages/Quantile regression" >}})

    + Semi-parametric method.

  + Bayesian?
