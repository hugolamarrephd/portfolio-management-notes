## Overview

Elliptical distributions are a broad class of probability distributions,
which can be thought of as a generalization of the multivariate normal distribution.

- **Contours**: The level curves or surfaces of the probability density function (if it exists) are ellipsoids centered on the location parameter $\mu$.
- **Linear Transformations**: Linear transformations of elliptically distributed vectors are also elliptically distributed.
- **Marginal Distributions**: Marginals of elliptically distributed vectors are also elliptically distributed.
- **Heavy Tail and Kurtosis Flexibility**: Elliptical distributions can model heavy tails and different levels of kurtosis.
- **Symmetrical and Lack of Skewness**: All marginals and conditionals of an elliptical distribution are symmetric about their means.

## Definition 

$X \in \mathbb{R}^N$ follows an *elliptical distribution* parameterized by a location parameter $\mu \in \mathbb{R}^{N}$,
a dispersion parameters $\Sigma \in \mathbb{R}^{N \times N}$, and a generator function $g: \mathbb{R}^+ \mapsto \mathbb{R}^+$
if its [[probability-density-function]] is given by

$$
\vert \Sigma \vert^{-\frac{1}{2}} g((x-\mu)^\top \Sigma^{-1} (x-\mu)) = 
\vert \Sigma \vert^{-\frac{1}{2}} g(\text{d}_M^2(x; \mu,\Sigma))
$$
where 

$$
\text{d}_M(x; \mu, \Sigma) \equiv \sqrt{(x-\mu)^\top \Sigma^{-1} (x-\mu)}
$$
is the [[mahalanobis-distance]]. Note that the generator will usually depend on the dimensionality of
$X$, i.e. $g$ will be parametrized by $N$.

We can define an elliptical distribution according to its [[characteristic-function]],

$$
\phi(\omega) = e^{i\omega^\top\mu} \psi(\omega^\top \Sigma \omega)
$$
where $\psi: \mathbb{R} \mapsto \mathbb{R}$ is a real-valued scalar function.

### Radial Representation

Alternatively, an elliptical distribution can always be represented as 

$$
X = \mu + A U
$$
where $\mu\in\mathbb{R}^{N}$ is the location parameter, $A\in\mathbb{R}^{N \times K}$ is related to $\Sigma$ according to $\Sigma= AA^\top$,
and $U\in\mathbb{R}^K$ is a *random vector* whose elements have a standardized spherical distribution.
Note that in practice, $A$ could be computed as the [[cholesky-decomposition]] of $\Sigma$.
The distribution of $U$ is determined by the generating function which can be decomposed as 

$$
U = rY
$$
where (1) $r\in\mathbb{R}^+$ is a non-negative random variable representing the radial component of $X$, viz.

$$
r = d_M(x;\mu, \Sigma),
$$

(2) $Y\in\mathbb{R}^N$ is a random vector **uniformly distributed** on the unit-sphere
(i.e. random vector of length one) and (3) $r$ and $Y$ are **independent**.
We can show the [[probability-density-function]] of r can be related to $g$ according to

$$
f_r(r) = 2 \frac{\pi^\frac{N}{2}}{\Gamma(\frac{N}{2})} r^{N-1} g(r^2)
$$

such that an elliptical distribution could alternatively be characterized
by the [[probability-density-function]] of its radial component instead of its generator function.

## Simulation

In practice, the most convenient way to simulate from the elliptical distribution 
is to rely on its radial representation. 
The uniformly distributed term $Y$ can be simulated according to

$$
Y_i \gets \frac{Z_i}{\vert\vert Z_i \vert\vert}
$$
where $\{Y_i\}$ represents a set of random draws for $Y$
and $\{Z_i\}$ represent random standard normal draws.
Standard normal draws are usually readily available from existing software.
We next simulate the radial components according to the desired generator, and
obtain a set $\{r_i\}$.
We can finally simulate X according to $X_i = \mu + r_i A Y_i$.

## Moments
The expectation and covariance of an elliptical distribution are respectively given by

$$
\text{E}[X] = \mu 
$$
and 

$$
\text{Cov}[X] = \frac{1}{N}\text{E}[\text{d}_M^2(X; \mu, \Sigma)] \Sigma = \frac{1}{N}\text{tr}(\Sigma^{-1}\text{Cov}[X])\Sigma
$$
where the second equation follows by noting that

$$
\text{E}[\text{d}_M^2(X; \mu, \Sigma)] = \text{E}[(x-\mu)^\top \Sigma^{-1} (x-\mu)] = 
\text{tr}(\Sigma^{-1}\text{Cov}[X])
$$
using the expectation of quadratic forms from [[linear-algebra-identities]].

## Properties

An elliptical distribution remains elliptical following an affine transformation of the random variable $X$. More precisely, if $X \sim \text{Elliptical}(\mu,\Sigma,g)$, we have

$$
a + BX \sim \text{Elliptical}(a+B\mu, B\Sigma B^\top, \tilde g)
$$
where $\tilde g$ will generally be different than $g$. This result reenforce our intuition of $\mu$ and $\Sigma$ as being respectively related to location (i.e. expectation) and dispersion (i.e. covariance).
Indeed, we know from the properties of basic probability operators that
$\text{E}[a+BX] = a + B\text{E}[X]$ and $\text{Cov}[a+BX] = B\text{Cov}[X]B^\top$.
## Examples
### Normal Distribution

In the case of a normal distribution $X\sim\mathcal{N}(\mu,\Sigma)$, we have $g(z) = (2\pi)^{-\frac{n}{2}} e^{-\frac{z}{2}}$,  or equivalently, $\psi(z) = e^{-\frac{1}{2}z}$.

The covariance is simply given by $\text{Cov}[X] = \Sigma$.
## Student-t

In the case of a Student-t distribution $X\sim t(\mu,\Sigma, \nu)$ with $\nu\in\mathbb{R}^+$, we have

$$
g(z) = \frac{\Gamma(\frac{\nu+N}{2})}{\Gamma(\frac{\nu}{2})(\nu\pi)^\frac{N}{2}} (1 + \frac{z}{\nu})^{-\frac{\nu+N}{2}}
$$
where $\Gamma$ is the [[gamma-function]]. This generator converges to the normal generator as $\nu\rightarrow\infty$ , which is consistent with the fact that the Student-t distribution converges to the normal distribution as $\nu$ increases.

The expectation (when $\nu>1$) is $\text{E}[X] = \mu$ and the covariance (when $\nu>2$) is $\text{Cov}[X] = \frac{\nu}{\nu-2}\Sigma$,
which does not exactly match with $\Sigma$.
We can show that the Student-t generator function (and the number of degrees of freedom)
is preserved by linear transformation such that if $X \sim t(\mu, \Sigma, \nu)$

$$
a + BX \sim t(a + B\mu, B\Sigma B^\top, \nu)
$$

From this result, we readily see that components of $X$ are *never* independent, *even when they are uncorrelated* (i.e. when $\Sigma$ is diagonal).
If they *were* independent, the [[central-limit-theorem]] would apply and
the sum of the components (i.e. obtained by setting $B=\begin{bmatrix} 1 & \ldots & 1\end{bmatrix}$ in the previous
expression) would be normal.

The radial decomposition can be re-written as 

$$
X = \mu + \frac{\Sigma Z}{\sqrt{V/\nu}}
$$
where $Z \sim \mathcal{N}(0,I)$, $V \sim \chi_\nu^2$  and $Z$ and $V$ are *independent*.




