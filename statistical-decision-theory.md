---
tags:
  - math
---

# Intro
## What is it?
Attempt to combine a model of uncertainty with other considerations of a problem such as
* the consequences of a decision
* any prior knowledge
*in order to make the best possible decision*.

## Notation
* Let $s \in S$ be the *state of nature* with state space denoted by $S$
	* $s$ can also be thought of as *unknown parameters*
* Let $a \in A$ an *action* with action space denoted by $A$
* Let $X\in\mathcal{X}$ a random variable in sample space denoted by $\mathcal{X}$
	* x denotes a realization of X
	* the density of X *for a given state of nature* is denoted by $f(x\vert s)$
* Let $\pi(s)$ be the prior density of $s$ and $\tilde\pi(s)$ the corresponding posterior distribution

Henceforth, a superscript on the expectation operator $E$ refers to the source of randomness 
(random variable, density, etc)
A subscript on $E$ refers to parameters which are assumed given, fixed and non-random.

## Loss Function
We are interested in the loss function denoted by

$$
l(s,a)  \geq -K > -\infty
$$

* The state of nature $s$ is not known when an action is taken and the choice of $a$ does not affect the distribution of $s$
* Loss increases for worst state outcome/action pairs
* Loss is a random variable since $s$ is a random variable

## Decision Definition
A *decision rule* $d$, a mapping from sample $x$ to actions $a$

$$
d: x\in X \mapsto a \in A
$$

* $d$ can be thought of as an *estimator*

### Randomized Decisions
A randomized decision rule $\tilde d$ is a density over $A$ such that $\tilde d(x, a)$ is the probability of $a$
*given that x was observed*.
Note that a non-random decision rule can be randomized by assuming that one of the action
has probability one (and all others have probability zero).

### Equivalent Decisions
Decision rules $d_1$ and $d_2$ are equivalent iff $P_s[d_1(X) = d_2(X)] = 1 \quad \forall s$.

## Bayesian Expected Loss
The Bayesian expected loss is **averaging losses over states of nature.**
The Bayesian expected loss of an action is defined by

$$\rho(\tilde\pi,a) \equiv E^{\tilde\pi}[l(s,a)]$$

where the expectation is taken with respect to the state of nature $s$ under density $\tilde\pi$,
with $\tilde\pi$ the **posterior** distribution taking into account data $x$.

## Frequentist Risk
Frequentist risk is **averaging over data samples.**

The **risk function** is defined as 

$$R(s, d)\equiv E^X_s[l(s, d(X))]$$

where the expectation is taken with respect to the *sample uncertainty*,
under the assumption of a fixed state of nature $s$.

### R-better and Admissibility
A decision rule $d_1$ is R-better than $d_2$ if

$$R(s, d_1) \leq R(s, d_2) \quad \forall s$$

A decision rule $d$ is *admissible* if there exists no R-better decision rule.

## Bayes Risk
**Averaging over both data samples and states of nature.**
The Bayes risk of a *decision rule* with respect to *prior* distribution $\pi$ is

$$r(\pi, d) = E^\pi[R(s,d)] = E^\pi[E^X_s[l(s,d(X))]]$$

## Regret
Regret given by

$$l(s,a) - \min_{a^\prime \in A} l(s,a^\prime)$$

is always positive and reaches its minimum at zero.

Reward is simply the negative of the loss

$$Y \equiv -l$$

When the state space is the same as the action space, it is common to let $l$ be a *divergence* such as the *squared Euclidean distance*.

### Bayes Risk

>**Idea.** Rank actions based on average loss.

Bayes risk is given by

$$\rho(a) \equiv E[l(s,a)]$$

and Bayes action is thus

$$a^\star \equiv \text{arg}\min_{a \in A} \rho(a)$$

If we have conditioning information $x$, let the **posterior Bayes risk**

$$\rho(a \vert x) \equiv E[l(s,a)\vert X=x]$$

and the **optimal posterior decision** is thus 

$$d(x) \equiv a^\star|x \equiv \text{arg}\min_{a \in A} \rho(a|x)$$

### Frequentist interpretation

Frequentist risk is defined by

$$r(s; d) \equiv E[l(S, d(x))\vert S=s]$$

where the expectation is taken over conditional information $x$ (or equivalently over actions given by decisions $d$).

In this context, the **Bayes risk** of decisions $d$ is

$$\rho(d) \equiv E[r(s;d)]$$

where the expectation is taken over $S$. **Bayes decisions** minimizes $\rho(d)$ which boils down to

$$\boxed{d^\star \equiv \text{arg}\min_{d\in D} E[l(S, d(X))]}$$

where the expectation is taken over the joint density of $(S,X)$.

$d$ is admissible iff

$$\nexists d^\prime \ni r(s;d^\prime(x)) \leq r(s;d(x)), \forall s   $$

### Minimax
TODO
# References

* [[_ref/berger-1985]]
