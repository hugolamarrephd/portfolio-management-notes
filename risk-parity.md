---
tags:
  - allocation
---

# The problem
The marginal risk contributions of a portfolio are
$$
\text{MRC}\equiv\frac{d\sqrt{w^\top\Sigma w}}{dw} = \frac{1}{2}\frac{(\Sigma + \Sigma^\top) w}{\sqrt{w^\top\Sigma w}} = \frac{\Sigma w}{\sqrt{w^\top\Sigma w}}
$$
The risk contributions are thus 
$$
\text{RC} \equiv w \odot \frac{\Sigma w}{\sqrt{w^\top\Sigma w}}
$$
where $\odot$ denotes elementwise product. Using the Euler decomposition theorem, we can easily show (see below) these risk contributions sum to the total risk of the portfolio.
The relative risk contributions are 
$$
\text{RRC} \equiv \frac{1}{\sqrt{w^\top\Sigma w}} RC = w \odot \frac{\Sigma w}{w^\top\Sigma w}
$$
A *risk-parity* portfolio is such that 
$$
RRC_i = \frac{1}{n} \quad \text{ for } i=1,\ldots,n
$$
>Solving for the risk-parity portfolio is generally difficult and a solution may not even exist under complex portfolio constraints.
# Euler interpretation

Since $f(w)\equiv \sqrt{w^\top\Sigma w}$ is homogenous of degree one (i.e. $f(cw)=cf(w)$), we have
$$
f(w) = w^\top \frac{df(w)}{dw} 
$$
such that the sum of RCs (defined previously) is the risk of the portfolio.
# Relationship with [[mean-variance-optimization]]

The risk parity portfolio is mean-variance efficient when
1. Sharpe ratios of all assets are identical
2. Correlations among assets are identical
## One-Over-Volatility Portfolio
In the special case when correlations among assets is also zero, the [[mean-variance-optimization]] mean-variance portfolio is given by
$$
w_i=\frac{1}{\lambda}\frac{\mu_i}{\sigma_i^2} = \frac{\gamma}{\lambda} \frac{1}{\sigma_i} 
$$
where $\gamma$ is the fixed Sharpe ratio.
We first note that 
$$
\left(w \odot \Sigma w\right)_i = \left(\frac{\gamma}{\lambda}\right)^2 
$$
such that relative risk contributions are
$$
\text{RRC}_i = \left(w \odot \frac{\Sigma w}{w^\top\Sigma w}\right)_i = \frac{(\gamma/\lambda)^2}{\sum_i (\gamma/\lambda)^2} = \frac{1}{N}
$$
and $w$ is a risk parity portfolio. We call
$$
w_i \equiv \frac{1}{\sigma_i}
$$
the **naïve risk parity** portfolio.
In the special case when correlations among assets are all equal to $\rho$, this portfolio is still optimal. Indeed, we have
$$
\text{RRC}_i = w_i \left(\rho\sum_{i\neq j} (\sigma\sigma^\top)_{ij} + (\sigma\sigma^\top)_{ii}\right)
$$
TODO
# The long-only case
Solving for
$$
\min_{w>0} w^\top\Sigma w - \sum_i \log w_i
$$
At the optimum, the following equation must hold
$$
((\Sigma + \Sigma^\top)w)_i - \frac{1}{w_i}= 0 \iff 2 w \odot(\Sigma w) = 1
$$
such that the risk contributions of all assets are equal. Note that the portfolio weights may not sum to one, but they can easily be re-scaled.