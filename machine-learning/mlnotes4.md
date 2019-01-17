---
layout: default
mathjax: true
---

Let's remind ourselves Newton's method:

$$\theta^{(t+1)} = \theta^{(t)} - \frac{f(\theta^{(t)})}{f'(\theta^{(t)})}$$

So we may use it to maxime the value of $l(\theta)$ by finding such $\theta$ s.t. $l'(\theta) = 0$

Time to bring the infinite dimensions:

$$\theta^{(t+1)} = \theta^{(t)} - H^{-1}\nabla_{\theta}l$$,

where $H^{-1}$ is an inverse of Hessian matrix.

Generalized Linear Models:

Recall that for $P(y\vert x;\theta)$ for $y \in \mathbb{R}$: Gaussian -> Least squares method 
$y \in \\{ 0 , 1\\}$: Bernoulli -> Logistic regression.

So where does $\frac{1}{1+e^{-z}}$ comes from? The answer comes from GLM, which can be written in a from:

$$P(y;\eta) = b(y) e^{\eta^{T}T(y) - a(\eta)}$$, where

$\eta$ - natural parameter
$T(y)$ - sufficient statistic (Usually T(y)=y)

Let's show that Linear and Logistic regressions are special cases of the form above.

Start with Bernoulli:

$Ber(\phi)$: $P(y=1; \theta) = \theta$

$P(y;\phi) = \phi^{y}(1-\phi)^{1-y} = e^{log\phi^{y}(1-\phi)^{1-y}}$
$ = e^{y log\phi+(1-y)(1-\phi)} = e^{log{\frac{\phi}{1-\phi}} y + log(1-\phi)}$, where

$y$ is $T(y)$

$b(y)=1$ 

$ log(1-\phi)$ is $-a(\eta)$

$\eta = log{\frac{\phi}{1-\phi}} \rightarrow \phi = \frac{1}{1+e^{-\eta}}$

And now with Gaussian:

Since (as stated in previous lecture) $\sigma^{2}$ doesn't affect the maximum likelihood, we will set it equal to 1. (But there is a broader generalization of GLM, which deals with one more parameter: dispersion. This would be mentioned later in this course).

$P(y;\mu) = \frac{1}{\sqrt{2\pi}}e^{-\frac{1}{2}(y-\mu)^{2}}$ 
$=\frac{1}{\sqrt{2\pi}}e^{-\frac{1}{2}y^{2}}e^{\mu y - \frac{1}{2}\mu^{2}}$

So now we can see that:

$T(y) = y$

$b(y)=\frac{1}{\sqrt{2\pi}}e^{-\frac{1}{2}y^{2}}$ 

$\eta = \mu$

$ a(\eta) = \frac{1}{2}\eta^{2}$








