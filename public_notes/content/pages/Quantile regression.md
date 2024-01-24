---
title: Quantile regression
tags:
categories:
date: 2024-01-23
lastMod: 2024-01-23
---
# Resources

  + [Quantile regression - Wikipedia](https://en.m.wikipedia.org/wiki/Quantile_regression)

  + https://sites.google.com/site/econometricsacademy/econometrics-models/quantile-regression

    + Pretty good. Watch the videos.

![L1.pdf](/assets/l1_1705778240731_0.pdf)

    + Has a lot of extra stuff that i have not looked at yet.

![lec9.pdf](/assets/lec9_1705798395667_0.pdf)

    + goes into the maths.

# The model

  + A linear model:

    + $$y_i = x_i \beta_q + \epsilon_i$$

    + a \beta for every quantile.

  + To compute OLS, we use the following loss function:

    + $$\min\sum e_i^2$$

  + Use a new loss function that penalizes differently for under estimation and over estimation.

  + It is apparently linear/proportional(? idk the term)

    + To get 5%ile

    + penalize underestimation and overestimation in the ratio 5:95.

  + For quantile $$q$$,

    + $$\min q\sum_{y_i \ge \hat{y_i}} |e_i|  + (1-q)\sum_{y_i < \hat{y_i}}|e_i|$$

  + It is easy to see that for the median,

    + $$\min \sum |e_i|$$

# Interpretation

  + Pretty much the same as OLS.

  + The \beta s turn out to be the _marginal effects_

    + $$\frac{\partial Q(y | x)}{\partial x_i} = \beta_{qi}$$

  + at that quantile.

  + It is sorta nice with some what non linear patterns

![2024-01-20-11:45:19-screenshot.png](/assets/2024-01-20-11:45:19-screenshot_1705776334626_0.png)

  + Wikipedia claims:

    + Even when the actual function is non linear, given that the quantile regression still chooses the best linear approximation at that *point*,

      + > the slope parameters  $$\beta_q$$ of the linear model can be interpreted as weighted averages of the [partial] derivatives.

    + Dunno, where weighted average comes from though.

  + Basically, green light for causal inference B-).

# Hypothesis testing

  + The \betas are asymptotically normal, with some scary looking standard errors.

    + Use bootstrapping to calculate confidence intervals.

# Computation

  + [[Linear Programming]].

  + The object function is the loss function.


    + $$\min q\sum_{y_i \ge \hat{y_i}} |e_i|  + (1-q)\sum_{y_i < \hat{y_i}}|e_i|$$

    + where $$e_i = y_i - x_i\beta_q$$

    + It is indeed linear.

    + Linear in *parameters*, remember?

      + (we can actually use LP to do OLS also, btw. )

  + ## Fancy (correct) Specification


    + Objective fn

      + $$\underset{\beta,u^{+},u^{-}}{\min} \quad{q1^{'}u^{+}+(1-q)1^{'}u^{-}}$$

    + such that,

    + $$X\beta+u^{+}-u^{-}=Y\\ \text{non-negativity constraints on u s}.$$

    + Not sure how the betas are made to be over the entire real line

      + maan, you go do LP again.

    + Note that,

      + $u^+$ is the underestimation

      + $u^-$ is the overestimation.

  + ## For q = 0.5

    + The median makes calculations sorta easy

    + Objective function

      + $$\min_\beta   1'|Y - X\beta|$$

    + We can rewrite that as,

      + just a linear algebra trick for converting mods.

      + $$\min_\beta 1't$$

    + where,

      + $$-t  \le Y - X\beta \le t $$

  + ## R implementation

```r
library(quantreg)

# OLS regression
olsreg <- lm(Y ~ X, data=mydata)
# Quantile regression
quantreg25 <- rq(Y ~ X, data=mydata, tau=0.25)

# Plotting data
quantreg.all <- rq(Y ~ X, tau = seq(0.05, 0.95, by = 0.05), data=mydata)
quantreg.plot <- summary(quantreg.all)
plot(quantreg.plot)
```

# Math fax

  + In general,

  + $$\bar{x} = \argmin_y \sum (x - y)^2 $$

  + $$\text{median} = \argmin_y \sum |x - y|$$

  + This gives you the MLE for a laplace distribution in the same way the least squares gives the MLE for a normal distribution.

# Assumptions

  + I really don't them, but i guess they are the gauss-markov ones only?

  + and for significance testing, $$\epsilon_i \sim N(0, \sigma^2)$$

# Equivariance

  + Invariant to monotonic transformations,

    + $$Q_{h(Y)|X}(q|X) = h(Q_{Y|X}(q|X))$$

  + Example,

    + take $$Q_{Y|X}(q)=X\beta_{q}$$

    + then,

    + $$Q_{exp(Y)|X}(q)=\exp(X\beta_{q})$$

  + The mean regression does not work,

    + $$\operatorname{E} (\ln(Y))\neq \ln(\operatorname{E}(Y)).$$

    + Mean regression only works for linear transforms, while quantile ones can handle any monotonic transformation. Pretty cool.

# Heteroskedasticity

# Panel data methods

![SimpleQRpanel_EJ.pdf](/assets/simpleqrpanel_ej_1705785570515_0.pdf)

  + Because quantiles are not linear operators like expectations,

    + $$Q_{a+b}(q) \ne Q_a(q) + Q_b(q)$$

  + Demeaning (or differencing)  is not possible.

  + So, fixed effects require something fancy.

    + read the above pdf.

# Misc

  + Expectiles.

    + The quantiles but with squared loss instead of deviation.

    + what does it even mean?

      + nothing.

  + bootstrapped quantile regression (BQR) analysis.

    + bootstrap amplifies the outliers.

  + Quantile regression averaging

  + [[Composite Quantile Regression]]
