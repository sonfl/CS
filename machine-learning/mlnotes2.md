---
layout: default
mathjax: true
---
$\theta$ is a parameter,
$x$ is an input variable,
$y$ is an output variable,
$\alpha$ is a learning rate(arbitrary)

Simple linear regression function: 

$$ h(x) = \sum_{i=0}^{n}\theta_{i}x_{i} = \theta^{T}x$$

Let's define the error function as least squares:

$$ J(\theta) = min_{\theta}\frac{1}{2}\sum_{i=1}^{m}(h_{\theta}(x^{(i)}) - y^{(i)})^{2}$$

Since $J(\theta)$ is a convex function(see Questions), we will get such a gradient descent:

$$ \theta_{i} := \theta_{i} - \alpha\frac{\partial}{\partial\theta_{i}}J(\theta)$$

Let's derive $\frac{\partial}{\partial\theta_{i}}J(\theta)$ for only one training example: 

$$\frac{\partial}{\partial\theta_{i}}J(\theta) =\frac{\partial}{\partial\theta_{i}}\frac{1}{2}(h_{\theta}(x)-y)^{2} = $$

$$=2\frac{1}{2}(h_{\theta}(x)-y)\frac{\partial}{\partial\theta_{i}}(h_{\theta}(x)-y) = $$

$$=(h_{\theta}(x)-y)\frac{\partial}{\partial\theta_{i}}(\theta_{0}x_{0}+...+\theta_{n}x_{n}-y) =(h_{\theta}(x)-y)x_{i}$$

We can transform it to the matrix form, given:

$\nabla_{\theta}J = \begin{pmatrix}\frac{\partial J}{\partial\theta_{0}} \\\\ \vdots \\\\ \frac{\partial J}{\partial\theta_{n}}\end{pmatrix} \in \mathbb{R}^{n+1}$, then $\Theta = \Theta - \alpha \nabla_{\theta}J$

$X\Theta = \begin{pmatrix}(x^{(1)})^{T} \\\\ \vdots \\\\ x^{(m)})^{T}\end{pmatrix}\Theta$ , 
$X\Theta = \begin{pmatrix}(x^{(1)})^{T}\Theta \\\\ \vdots \\\\ (x^{(m)})^{T}\Theta\end{pmatrix} = \begin{pmatrix} h_{\theta}(x^{(1)}) \\\\ \vdots \\\\ h_{\theta}(x^{(m)})\end{pmatrix}$

$X\Theta - y = \begin{pmatrix} h(x^{(1)}) - y^{(1)} \\\\ \vdots \\\\ h(x^{(m)}) - y^{(m)}\end{pmatrix}$

Since $z^{T}z = \sum_{i}z_{i}^{2}$, then

$\frac{1}{2}(X\Theta - y)^{T}(X\Theta - y) = \frac{1}{2}\sum_{i=1}^m((x^{(i)}) - y^{(i)})^{2}) = J(\Theta)$

If we [skip some steps of moving stuff around](http://cs229.stanford.edu/notes/cs229-notes1.pdf), we get:

$\nabla_{\theta} J(\Theta) = X^{T}X\Theta - X^{T}y = 0$

$X^{T}X\Theta = X^{T}y$

$\boxed{\Theta = (X^{T}X)^{-1}X^{T}y}$

All interesting questions see in the Questions section!
