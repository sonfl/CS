---
layout: default
mathjax: true
---

> Some of the missed steps in calculations might be in the Questions section. Or might not...

"Parametric" learning algorithm
    - $\theta$'s fixed set of parameters
"Non-parametric" learning algorithm
    - # of params growns with m

As an example of non-parametric algorithm we have Locally weighted regression defined in such a form:

$$\sum_{i}w^{(i)}(y^{(i)}-\Theta^{T}x^{(i)})^{2}$$, where $w^{(i)} = e^{-\frac{(x^{(i)}-x)^{2}}{2}}$

$w^{(i)}$ has nothing to do with Gaussian's, just in case.

Probabilistic interpretation:

This interpretation is full of assumption, which will be introduced along the way, so get ready:

Assume $y^{(i)} = \Theta^{T}x^{(i)}+\epsilon^{(i)}$, where $\epsilon^{(i)}$ is an error term

$\epsilon^{(i)} \sim \mathcal{N}(0,\sigma^{2})$ 

$P(\epsilon^{(i)}) = \frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(\epsilon^{(i)})^{2}}{2\sigma^{2}}}$

$P(y^{(i)} \vert x^{(i)};\theta) = \frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(y^{(i)} - \theta^{T}x^{(i)})^{2}}{2\sigma^{2}}}$, where 

$(y^{(i)} \vert x^{(i)};\theta) \sim \mathcal{N}(\theta^{T}x^{(i)}, \sigma^{2})$

So, let's review these lines: as Andrew notices errors are usually normally distributed. Let's remember central limit theorem that says that when independent variables are added its sum tends to normal distribution. Here is our next assumption: $\epsilon^{(i)}$ are independently identical distributions. 

So bearing that in mind, we can deduce that every outcome (y in our example) has some noise, with the same variance as the error, since error is the reason of that normal distribution.

So the likelihood function would look like this:

$L(\theta) = P(\vec{y} \vert X;\Theta)
= \prod_{i=1}^{m}P(y^{(i)} \vert x^{(i)};\theta)
=\prod_{i=1}^{m}\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(y^{(i)} - \theta^{T}x^{(i)})^{2}}{2\sigma^{2}}}$

To be more clear, we mean likelihood of parameters and probability of data.

Maximum likelihood: choose $\theta$ to maximize $L(\theta)$

To make our lives easier let's introduce 

$l(\theta) = logL(\theta) = 
log\prod_{i=1}^{m}\frac{1}{\sqrt{2\pi}\sigma}e^{(...)}$

$= \sum_{i=1}^{m}log(\frac{1}{\sqrt{2\pi}\sigma}e^{...}) = mlog\frac{1}{\sqrt{2\pi}\sigma} + \sum_{i=1}^{m}-\frac{(y^{(i)} - \theta^{T}x^{(i)})^{2}}{2\sigma^{2}}$

So maximazing $l(\theta)$ is the same as minimazing $\frac{\sum_{i=1}^{m}(y^{(i)} - \theta^{T}x^{(i)})^{2}}{2} = J(\theta)$

As we can see here $\sigma^{2}$ doesn't really matter. Whatever the sigma is, we'll end up with $J(\theta)$. We will comeback to it later.

Welcome to the logistic regression, buddy!
Basically it's not quite linear regression since $y \in \\{0,1\\}$. Also it's usually a bad idea to apply logistic regression to linear one. 

Sooooooo, let's define the function for this type of regression!

$h_{\theta}(x) = g(\theta^{T}x) = \frac{1}{1+e^{-\theta^{T}x}}$, where $g(z)$ is a sigmoid function

<img src="/CS/public/Plot-of-the-sigmoid-function.png">

The reasons behind this very function will be later in this course.

$P(y=1 \vert x; \theta) = h_{\theta}(x)$

$P(y= \vert x; \theta) = 1 - h_{\theta}(x)$

$P(y \vert x; \theta) = h_{\theta}(x)^{y}(1 - h_{\theta}(x))^{1-y}$

Isn't it a neat way to write these eqs??

$L(\theta) = P(\vec{y} \vert X;\Theta) = \prod_{i}P(y^{(i)} \vert x^{(i)}; \theta)$

$=\prod_{i}h_{\theta}(x^{(i)})^{y^{(i)}}(1 - h_{\theta}(x^{(i)}))^{1-y^{(i)}}$

Hello good old $l(\theta)$

$l(\theta) = logL(\theta) = \sum_{i}(y^{(i)}logh_{\theta}(x^{(i)}) + (1-y^{(i)})log(1-h_{\theta}(x^{(i)})))$

So we can apply our already known gradient ascend to compute $\theta$:

$\theta = \theta + \alpha\nabla_{\theta}l(\theta)$

(please notice that we put a plus sign, because we need to find maximum, please refer to the Questions section of 2nd lecture)

By some woo-doo magic we get:

$\frac{\partial}{\partial \theta_{j}}l(\theta) = \sum_{i=1}^{m}(y^{(i)} - h_{\theta}(x^{(i)})x_{j}^{(i)}$

Which is exacly the same thing as in linear regression. Except $h_{\theta}(x^{(i)})$. Why it is so - see in the next lecture! 

