---
tags:
  - allocation
  - bayesian
---

# Probabilistic Interpretation

We assume normally distribution asset returns

$$
r \sim \mathcal{N}(\mu, \Sigma)
$$

where $\mu$ is a random variable

$$
\mu \sim \mathcal{N}(\pi, \tau\Sigma)
$$

and $\pi$ is typically computed as the implied excess returns of a market-weighted index;
see [[mean-variance-optimization]].
More precisely,

$$
\pi = \lambda \Sigma w_\text{mkt}
$$

where $\lambda$ is the risk aversion and $w_\text{mkt}$ are the weights.

Next, the investor introduces *noisy* portfolio views $(P,v,\Omega)$ such that

$$
v = P\mu + \epsilon
$$

where $\epsilon \sim \mathcal{N}(0,\Omega)$, or equivalently

$$
v \vert \mu \sim \mathcal{N}(P\mu, \Omega)
$$

which can be "inverted" using Bayes rule, ie.

$$
\mu \vert v \sim \mathcal{N}(\mu_\text{BL}, \Sigma^\mu_\text{BL})
$$

But we are ultimately interested in conditioning $r$ on our views according to

$$
r \vert v \sim \mathcal{N}(\mu_\text{BL}, \Sigma_\text{BL})
$$

From properties of conditional normal laws, we find

$$
\boxed{\mu_\text{BL} = \pi + \tau \Sigma P^\top (\tau P \Sigma P^\top + \Omega)^{-1} (v-P\pi)}
$$

and

$$
\Sigma_\text{BL} = (1+\tau) \Sigma - \tau^2 \Sigma P^\top (\tau P \Sigma P^\top + \Omega)^{-1} P \Sigma
$$

# Direct Views on Market
When the investor defines the views in terms of market returns directly,

$$
v = Pr + \epsilon
$$

where $\epsilon \sim \mathcal{N}(0,\Omega)$ and assuming **no** uncertainty on return expectations i.e.

$$
\mu = \pi
$$

We get similar results

$$
r | v \sim \mathcal{N}(\tilde\mu_\text{BL}, \tilde\Sigma_\text{BL})
$$

where

$$
\boxed{\tilde\mu_\text{BL} = \pi + \Sigma P^\top (P \Sigma P^\top + \Omega)^{-1} (v-P\pi)}
$$

and

$$
\tilde\Sigma_\text{BL} = \Sigma - \Sigma P^\top (P \Sigma P^\top + \Omega)^{-1} P \Sigma
$$

where $\tau$ has disappeared.

> This formulation has the nice property that $\mathcal{N}(\tilde\mu_\text{BL}, \tilde\Sigma_\text{BL})$ tends to the distribution $r \vert \{Pr = v\}$ where $r\sim\mathcal{N}(\pi, \Sigma)$ when $\Omega\rightarrow0$, which is **not** the case under the classical Black-Litterman formulation.
> This formulation thus makes it more consistent with "what-if" scenario analysis for which we test the impact of market events $\{Pr=v\}$ on returns.

# Confidence-based
It is easier to think in terms of conviction between 0 and 100% for individual views, instead of specifying the full uncertainty matrix.

For a single view, the 100%-confidence return expectation is 

$$
\mu_\text{100\%} = \pi + \Sigma p^\top \frac{v-p\pi}{p\Sigma p^\top} 
$$

where $p$ is a row of $P$, and of course the 0%-confidence return expectation is $\mu_\text{0\%} = \pi$.

*When there are no constraint to the portfolio optimization problem*, we can think of a linear continuum of overlays between $\mu_\text{0\%}$ and $\mu_\text{100\%}$.
Indeed, using [[mean-variance-optimization]] portfolio optimization, we have that the full confidence portfolio is given by

$$
\frac{1}{\lambda}\Sigma^{-1}\mu_\text{100\%} = \underbrace{\frac{1}{\lambda}\Sigma^{-1}\pi}_\text{initial portfolio} + \underbrace{\frac{1}{\lambda} p^\top \frac{v-p\pi}{p\Sigma p^\top}}_\text{overlay}
$$

In practice, it is easier to scale each 100%-confidence overlay

$$
\boxed{\frac{c}{\lambda} \frac{v-p\pi}{\sigma^2_p} p^\top }
$$

where $c\in[0,1]$ is the confidence parameter for that specific view and where we defined 

$$
\sigma^2_p \equiv p\Sigma p^\top
$$

for convenience.

Again for each individual view, we can solve for $\omega^2$ (an element on the diagonal of $\Omega$) that gives us the scaled overlay ie.

$$
\frac{1}{\lambda}\Sigma^{-1}\pi + \frac{c}{\lambda} p^\top \frac{v-p\pi}{\sigma^2_p} = \frac{1}{\lambda} \Sigma^{-1}\pi + \frac{1}{\lambda} \Sigma^{-1}\Sigma p^\top (\sigma^2_p + \omega^2)^{-1} (v-p\pi)
$$

$$
\iff c p^\top \frac{v-p\pi}{\sigma_p^2} =   p^\top \frac{v-p\pi}{\sigma_p^2 + \omega^2}
$$

$$
\iff \frac{c}{\sigma^2_p} =  \frac{1}{\sigma^2_p + \omega^2}
$$

$$
\iff c \sigma^2_p + c\omega^2- \sigma^2_p = 0 
$$

$$
\iff \boxed{\omega^2 = \frac{1-c}{c}\sigma^2_p} 
$$
