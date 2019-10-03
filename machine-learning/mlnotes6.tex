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

where $\Sigma$ is a covariance matrixs

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

Apparently, if we have multivariate gaussian we get logistical regression, but the converse is not true. So we may think of GDA as a stronger modelling. Therefore it is more efficient. But on the other hand, if we make incorrect assumptions, we would be better off with a weaker logistic regression, which would handle all inconsistencies with the data.


>Naive Bayes

Spam filter is a good example of Naive Bayes. Suppose we have a vector $x = \begin{pmatrix} 1 \\\\ 0 \\\\ 1 \\\\ 0 \\\\ \vdots \\\\ 0 \end{pmatrix}$ where 1 is a presence of some particular word and 0 is its abscence. Then this vector represents a particular mail which we'll try to classify.

Now we need to model $P(x \vert y)$. Now we will assume that $x_{i}$ is conditionally independent give y (which is rather not true, since if we get a mail where we have a word "Java", it's more probable to have other CS-related word), but it still works. This assumption has its name: Naive Bayes assumption.
$P(x_{1000} \vert y) = P(x_{1000} \vert y, x_{1200})$

(Note it's not a full independence of events)
Suppose our dictionary (vector x) has dimension of 50000.

$$P(x_{1},...,x_{50000} \vert y)
= P(x_{1} \vert y) P(x_{2} \vert y, x_{1}) ... P(x_{50000} \vert y, x_{1}, x_{2},...,x_{49999})$$
$$= P(x_{1} \vert y)P(x_{2} \vert y)...P(x_{50000} \vert y) = \prod_{j=1}^{n}P(x_{j} \vert y)$$

Our model is parameterized by $\phi_{j \vert y=1} = P(x_{j} = 1 \vert y=1)$,$\phi_{j \vert y=0} = P(x_{j} = 1 \vert y=0)$ and $\phi_{y} = P(y=1)$

Then for our training set {$(x{(i)},y^{(i)}); i = 1,...,m$} we can write likelihood:

$$L(\phi_{y=1}, \phi_{j \vert y=1}, \phi_{j \vert y=0}) = \prod_{i=1}^{m}P(x{(i)},y^{(i)})$$

After maximazing that likelihood we get:

$$\phi_{j \vert y=1} = \frac{\sum_{i=1}^{m}1\{x_{j}^{(i)} = 1 \wedge y^{(i)} = 1\}}{\sum_{i=1}^{m}1\{y^{(i)}=1\}}$$

$$\phi_{j \vert y=0} = \frac{\sum_{i=1}^{m}1\{x_{j}^{(i)} = 1 \wedge y^{(i)} = 0\}}{\sum_{i=1}^{m}1\{y^{(i)}=0\}}$$

$$\phi_{y} = \frac{\sum_{i=1}^{m}1\{y^{(i)} = 1\}}{m}$$

So we can easily compute such a thing:

$$ P(y=1 \vert x) = \frac{P(x \vert y=1) P(y=1)}{P(x)}$$ 
$$= \frac{(\prod_{j=1}^{n}P(x_{j} \vert y=1)) P(y=1)}{(\prod_{j=1}^{n}P(x_{j} \vert y=1))P(y=1) + (\prod_{j=1}^{n}P(x_{j} \vert y=0))P(y=0)}$$

And then we pick whichever has the higher probability.


>Laplace smoothing

If we get a new word we've never seen before,by our algorithm above, we automatically set $\phi_{y=1} = 0$ and $\phi_{y=0} = 0$ so $P(y=1 \vert x) = \frac{0}{0}$ which is undefined.

To combat an issue we may change a little bit a definition of $\phi_{j}$ to be:

$$\phi_{j} = \frac{\sum_{i=1}^{m}1\{z^{(i)} = j\} + 1}{m + k}$$
