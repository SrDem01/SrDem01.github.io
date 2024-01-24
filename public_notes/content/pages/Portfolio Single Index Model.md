---
title: Portfolio Single Index Model
tags:
categories:
date: 2024-01-23
lastMod: 2024-01-23
---
# Resources

  + [Single-index model - Wikipedia](https://en.wikipedia.org/wiki/Single-index_model)

# Model

  + It regresses the excess (over the risk free rate) return of a stock on the excess return of the market in the same period.

  + This market return is captured by a single index. Something like nifty 100 or s&p 500.

  + The regression eq:

    + $$r_{it} - r_f = \alpha + \beta_i (r_{mt} - r_f) + \epsilon_{it}$$

    + errors $$\sim N(0, \sigma^2)$$

    + market term represents the movement of the market caused by macroeconomic changes.

    + \beta are the responsiveness of the firm to these macroeconomic variables.

    + \epsilon represents firm-specific shocks.

# Covariance between stocks

  + Assumes that returns between stocks are uncorrelated post subtracting the market means.

    + $$Cov(R_{it}- \beta_i m_t, R_{jt} - \beta_j  m_t) = 0 \ $$

  + You can get the covariance by multiplying the \beta s and the market variance.

    + $$Cov(R_i, R_j) = \beta_j \beta_i \sigma^2$$

Basically, the point is to simplify Covariance calculations.
