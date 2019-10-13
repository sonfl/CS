---
layout: default
mathjax: true
---
[The task can be found here.](/CS/public/ps1.pdf)

Problem 2: Poisson regression and the exponential family
>Part (a):


$P(y;\lambda) = \frac{e^{-\lambda} \lambda^{y}}{y!}$

$\frac{e^{-\lambda} \lambda^{y}}{y!} = e^{ln(\frac{e^{-\lambda} \lambda^{y}}{y!})}
= \frac{e^{yln\lambda-\lambda}}{y!}$, where 

$b(y)=\frac{1}{y!}$

$\eta=ln\lambda$,  $\lambda = e^{\eta}$

$T(y)=y$

$a(\eta) = e^{\eta}$

>Part (b):

$g(\eta)=E(T(y);\eta) = E(y;\eta) = \lambda = e^{\eta} = e^{\theta^{T}x}$

>Part (c):

$logP(y^{i} \vert x^{i};\theta) = log(\frac{e^{\lambda} \lambda^{y}{y!}}) = -\lambda + ylog\lambda - log(y!) = ylog(e^{\theta^{T}x}) - e^{\theta^{T}x} - log(y!)$

$\frac{\partial f}{\partial \theta_{i}} = -x_{i}e^{\theta^{T}x} + yx_{i} = (y-e^{\theta^{T}x})x_{i}$

Therefore stochastic ascend is of the formula:

$\theta_{i+1} = \theta_{i} + \alpha(y-e^{\theta^{T}x})x_{i}$

>Part (d):






