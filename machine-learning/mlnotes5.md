---
layout: default
mathjax: true
---

Generative Learning is an approach to decide whether $x$ is in set 1 or set 2 of data. We do it by means of making the model to predict set 1 and another model to predict set 2. And assign $x$ to the set, where the probability is greater.

Therefore discriminative are of form: $p(y \vert x)$

Generative: $p(x \vert y)$ and $p(y)$

After we model our models(above), we can use Bayes rule to get:

$$p(y \vert x) = \frac{p(x \vert y)p(y)}{p(x)}$$

where $p(x) = p(x \vert y=1)p(y=1)+p(x \vert y=0)p(y=0)$

The first example of such a learning is

>Gaussian discriminant analysis(GDA)

In this model we assume that $p(x \vert y) is distributed according to multivariate normal distribution, which is:

$$p(x;\mu,\Sigma) = \frac{1}{(2\pi)^{n/2}\vert \Sigma \vert ^{\frac{1}{2}}}e^{-\frac{1}{2}(x-\mu)^{T}\Sigma^{-1}(x-\mu)}$$,

where $\Sigma$ is a covariance matrix

Let's have an example of GDA:

Our model will be as such:

$ y \sim$ Bernoulli($\phi$)

$x \vert y=0 \sim \mathcal{N}(\mu_{0}, \Sigma)$

$x \vert y=1 \sim \mathcal{N}(\mu_{1}, \Sigma)$

Therefore we have:

$p(y) = \phi^{y}(1-\phi)^{1-y}$

$p(x \vert y=0) = \frac{1}{(2\pi)^{n/2}\vert \Sigma \vert ^{\frac{1}{2}}}e^{-\frac{1}{2}(x-\mu_{0})^{T}\Sigma^{-1}(x-\mu_{0})}$

$p(x \vert y=1) = \frac{1}{(2\pi)^{n/2}\vert \Sigma \vert ^{\frac{1}{2}}}e^{-\frac{1}{2}(x-\mu_{1})^{T}\Sigma^{-1}(x-\mu_{1})}$

And now our dear log likelihood:

$l(\phi, \mu_{0}, \mu_{1}, \Sigma) = log \prod_{i=1}^{m}p(x^{(i)}, y^{(i)}) = log \prod_{i=1}^{m}p(x^{(i)} \vert y^{(i)})p(y^{(i)})$

To predict we need $argmax_{y}P(y \vert x) = argmax_{y}P(x \vert y)P(y)$

Also by some magic steps we can observe that somehow $p(y=1 \vert x; \Sigma, \mu_{0}, \mu_{1}) = \frac{1}{1+e^{-\theta^{T}x}}$, which we used to model $p(y=1 \vert x)$

So when we would prefer GDA over logistic regression and vica versa?

Apparently, if we have multivariate gaussian we get logistical regression, but the converse is not true. So we may think of GDA as a stronger modelling. Therefore it is more efficient. But on the other hand, if we make incorrect assumptions, we would be better off with weaker logistic regression, which would handle all inconsistencies with the data.

