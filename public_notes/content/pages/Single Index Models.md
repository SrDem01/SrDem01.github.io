---
title: Single Index Models
tags:
categories:
date: 2024-01-23
lastMod: 2024-01-23
---
# Resources

  + [Semiparametric regression - Wikipedia](https://en.wikipedia.org/wiki/Semiparametric_regression#Index_models)

![NonParametrics7.pdf](/assets/nonparametrics7_1705867687056_0.pdf)

    + The important one


![handbook.pdf](/assets/handbook_1705964343640_0.pdf)


![Composite quantile regression for SIM](/assets/736216774_1705992301428_0.pdf)

    + Quantile regression.

# Index Models

  + A form of [[Semi Parametric Regression]]

  + A link function on the linear combination.

    + if the function is known, then non-linear least squares.

    + Basically, [[Generalized Linear Models]].

  + We have to estimate the link function and the \beta

  + The main benefit is that there is no issue with high dimensionality

    + The only non parametric part is the unknown link function.

    + Pretty good ngl.

# Model

  + The regression model is

  + $$E(Y|X) = g(X\beta)$$

  + where $$g$$ is an unknown link function.

  + The name Single index comes from the single *scalar* value that comes out of the $$X\beta$$.

  + In this sense, all the normal regressions are also SIM.

    + with known link functions.

  + $g$ includes both location and level shift.

    + the $$X$$ does not have an intercept.

  + The \beta s also need to be normalized to identify the model from an infinite series of equivalent models.

    + $\beta'\beta = 1$ and the first beta is positive.

    + Or, set the first \beta = 1.

  + $X$ needs to have more than 2 dims.

    + otherwise, the \beta s are pretty much degenerate.

# Interpretation

  + The marginal effect of some $x_i$ on the conditional mean of $Y$ is

    + Chain rule.

    + $$\frac{\partial }{\partial x_i} g(X\beta) = \beta_i g^{-1}(X\beta)$$

# Methods

  + ## Ichimura's method

    + what is an NW estimator?

    + [[Newey-West estimator]]

  + [Kernel Regression]({{< ref "/pages/Kernel Regression" >}})

# Quantile regression

  + [[Composite Quantile Regression]]

  + ## MACE

    + ### Basic idea

      + It uses a generalized weighted loss function

        + This includes quantile regression.

      + It takes a local linear approximation at $x$ near some $X_i$ of the link function.

        + Taylor series?

        + $$g(X_i'\beta) \approx g(X_i'\beta) + g'(x'\beta)(X_i - x)'\beta$$

      + and minimizes its expected value of the loss function using this linear approximation of the prediction.

        + By minimizing the empirical average.

        + which for some reason is multiplied with a kernel function?

          + how did the kernel function come?

      + Now this can be solved in two minimization problems

        + One minimizes the loss wrt \beta given the two functions
logseq.order-list-type:: number

        + Again wrt the two functions given \beta
logseq.order-list-type:: number

      + You can also add a penalty parameter to the loss function

        + getting similar results to LASSO

      + This is repeated iteratively

        + estimate β in (2.10) with an iterative procedure 
ls-type:: annotation
hl-page:: 7
hl-color:: purple


      + to compute

        + $\hat{\beta}$

        + $\hat{g}(x)$

        + $\hat{g}'(x)$

# Misc.

  + [Portfolio Single Index Model]({{< ref "/pages/Portfolio Single Index Model" >}})
