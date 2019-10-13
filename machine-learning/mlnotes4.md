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

>Generalized Linear Models:

Recall that for $P(y\vert x;\theta)$ for $y \in \mathbb{R}$: Gaussian -> Least squares method 
$y \in \\{ 0 , 1\\}$: Bernoulli -> Logistic regression.

So where does $\frac{1}{1+e^{-z}}$ comes from? The answer comes from GLM, which can be written in a from:

$$P(y;\eta) = b(y) e^{\eta^{T}T(y) - a(\eta)}$$, where

$\eta$ - natural parameter
$T(y)$ - sufficient statistic (Usually T(y)=y)

Let's show that Linear and Logistic regressions are special cases of the form above.

>Start with Bernoulli:

$Ber(\phi)$: $P(y=1; \theta) = \theta$

$P(y;\phi) = \phi^{y}(1-\phi)^{1-y} = e^{log\phi^{y}(1-\phi)^{1-y}}$, $ = e^{y log\phi+(1-y)(1-\phi)} = e^{log{\frac{\phi}{1-\phi}} y + log(1-\phi)}$, where

$y$ is $T(y)$

$b(y)=1$ 

$ log(1 - \phi) $ is $-a(\eta)$

$\eta = log{\frac{\phi}{1-\phi}} \rightarrow \phi = \frac{1}{1+e^{-\eta}}$

>And now with Gaussian:

Since (as stated in previous lecture) $\sigma^{2}$ doesn't affect the maximum likelihood, we will set it equal to 1. (But there is a broader generalization of GLM, which deals with one more parameter: dispersion. This would be mentioned later in this course).

$P(y;\mu) = \frac{1}{\sqrt{2\pi}}e^{-\frac{1}{2}(y-\mu)^{2}}$ 
$=\frac{1}{\sqrt{2\pi}}e^{-\frac{1}{2}y^{2}}e^{\mu y - \frac{1}{2}\mu^{2}}$

So now we can see that:

$T(y) = y$

$b(y)=\frac{1}{\sqrt{2\pi}}e^{-\frac{1}{2}y^{2}}$ 

$\eta = \mu$

$ a(\eta) = \frac{1}{2}\eta^{2}$

>Constructing GLMs:

Andrew introduces a few assumptions:

1) Given $y \vert x; \theta$ $\sim$ ExpFamily($\eta$) 

2) $T(y) = y$, so that means $h(x)=E(y \vert x; \theta)$

3) $\eta_{i} = \theta_{i}^{T}x$

With these assumptions we can easily prove Gaussian:

$h_{\theta}(x) = E(y \vert x; \theta) = \mu=\eta=\theta^{T}x$

Logistic regression:

$h_{\theta}(x) = E(y \vert x; \theta) = \phi=\frac{1}{1+e^{-\eta}}=\frac{1}{1+e^{-\theta^{T}x}}$

>Softmax Regression:
It's a form of classification, where $y \in \\{1,2,...,k\\}$

$\phi_{1},...,\phi_{k}$ are probabilities of these outcome. Although there is a concept of parameter redundancy, which mean that $P(y=k; \theta)=1-\sum_{i=1}^{k-1}\phi_{i}$

Also we would like to define $T(y) \in \mathbb{R^{k-1}}$ in a form:

$$T(1)=\begin{pmatrix}1 \\ 0 \\ 0 \\ \vdots \\ 0 \end{pmatrix}, \ T(2)=\begin{pmatrix}0 \\ 1 \\ 0 \\ \vdots \\ 0 \end{pmatrix}, \ T(k-1)=\begin{pmatrix}0 \\ 0 \\ 0 \\ \vdots \\ 1 \end{pmatrix}, \ T(k)=\begin{pmatrix}0 \\ 0 \\ 0 \\ \vdots \\ 0 \end{pmatrix}$$


We will $(T(y))_{i}$ write to denote i-th entry in a vector $T(y)$. Also let's define an indicator $1\\{\cdot \\}$: 

$1\\{True \\} = 1$ and $1\\{False \\} = 0$. Also you can verify that $1\\{y=i \\} = (T(y))_{i}$ 

Therefore we have:

$P(y;\theta) = \phi_{1}^{1\\{y=1 \\}}  \phi_{2}^{1\\{y=2 \\}} ...  \phi_{k}^{1\\{y=k \\}}$

$= \phi_{1}^{\(T(y\))\_{1}} \phi_{2}^{\(T(y\))\_{2}} ...  \phi_{k}^{1-\sum_{i=1}^{k-1}\(T(y\))\_{i}}$

$= e^{\(T(y\))\_{1})log(\phi_{1}) + \(T(y\))\_{2}log(\phi_{2})  + ... + (1-\sum_{i=1}^{k-1}\(T(y\))\_{i})log(\phi_{k})}$

$=e^{\(T(y\))\_{1})log(\frac{\phi_{1}}{\phi_{k}}) + \(T(y\))\_{2}log(\frac{\phi_{1}}{\phi_{k}})  + ... + log(\phi_{k})}$

which is of GLM form, where

$\eta=\begin{pmatrix}log(\frac{\phi_{1}}{\phi_{k}}) \\\\ log(\frac{\phi_{2}}{\phi_{k}}) \\\\ \vdots \\\\ log(\frac{\phi_{k-1}}{\phi_{k}}) \end{pmatrix}$

$a(\eta) = -log(\phi_{k})$

$b(y) = 1$

From that we can get such facts:

$e^{\eta_{i}} = \frac{\phi_{i}}{\phi_{k}}$

$\phi_{k}e^{\eta_{i}} = \phi_{i}$
 
$\phi_{k} \sum_{i=1}^{k}e^{\eta_{i}} = \sum_{i=1}^{k}\phi_{i}=1$

Therefore we can conclude $\phi_{i} = \frac{e^{\eta_{i}}}{\sum_{j=1}^{k}e^{\eta_{j}}}$

$P(y = i \vert x; \theta) = \phi_{i}$ 
$= \frac{e^{\eta_{i}}}{\sum_{j=1}^{k}e^{\eta_{j}}}$
$=\frac{e^{\theta_{i}^{T}x}}{\sum_{j=1}^{k}e^{\theta_{j}^{T}x}}$

By maximazing log-likelihood of the equation above we can get softmax regression ready.







