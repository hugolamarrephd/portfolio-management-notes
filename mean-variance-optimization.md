---
tags:
  - mean-variance
  - allocation
---
# Solution
We solve the *unconstrained* mean-variance portfolio $w$ according to
$$
\max_w w^T \mu - \frac{\lambda}{2} w^T \Sigma w
$$
where $\mu$ is a vector of return expectations, $\lambda$ is a risk aversion, and
$\Sigma$ is a covariance matrix.

This problem is strictly concave if $\Sigma$ is positive-definite. 
Assuming $\Sigma$ is positive-definite, we can try to nullify the gradient
$$
\frac{d}{dw} w^T \mu - \lambda w^T \Sigma w = \mu - \frac{\lambda}{2} (\Sigma + \Sigma^T) w = 0
$$
Since $\Sigma$ is symmetric, we finally have
$$
\mu - \lambda \Sigma w = 0 \implies \boxed{w=\frac{1}{\lambda}\Sigma^{-1}\mu}
$$
which must correspond to the maximum because of the concavity of the objective function.
# Implied Excess Return

We can also look at $\mu$ as a function of weights
$$
\boxed{\pi\equiv\mu=\lambda \Sigma w}
$$
which is used e.g. in the [[black-litterman]] framework.