---
layout: default
mathjax: true
---

> SVM

Remind yourself a logistic regression.

Compute $\theta^Tx$.

It predicts '1' iff $\theta^Tx >> 0$.

It predicts '0' iff $\theta^Tx << 0$.

If $\theta^Tx >> 0$, then it's very confident that y=1
If $\theta^Tx << 0$, then it's very confident that y=0

Suppose we have a lin. separable training set.

Also we'lll change the notation a little.

 $y \in \{-1, +1\}$, 
 
 $h_\theta(x)=g(\theta^Tx)$ -- we change this into:  $h_{w,b}(x)=g(W^Tx+b)$, where b is $\theta_0$

 >Definition: Functional margin of a hyperplane

(w,b) wrt $(x^{(i)}, y^{(i)})$ is $\hat{\gamma}^{(i)} = y^{(i)}(w^Tx^{(i)}+b)$

if $y^{(i)}=1$, we want $w^Tx^{(i)}+b >> 0$.

if $y^{(i)}=-1$, we want $w^Tx^{(i)}+b << 0$.

If $y^{(i)}(w^Tx^{(i)}+b)>0$, then we classified it correctly.

$\gamma = \min_{i} \hat{\gamma}^{(i)}$


> Geometric margin:

$(x^{(i)},y^{(i)})$  on a separating plane has a form of:
$x^{(i)} - \gamma^{(i)}\frac{w}{||w||}$

therefore, since the eq of a plane is $w^Tx+b=0$, then $w^T(x^{(i)} - \gamma^{(i)}\frac{w}{||w||})+b=0$

So the distance between training example and the hyperplane is:

$w^Tx^{(i)}+b=\gamma^{(i)}\frac{w^Tw}{||w||}=\gamma^{(i)}||w||$

$\gamma^{(i)}=(\frac{w}{||w||})^Tx^{(i)}+\frac{b}{||w||}$

More generally the geometric margin:

$\gamma^{(i)}=y^{(i)}[(\frac{w}{||w||})^Tx^{(i)}+\frac{b}{||w||}]$

If $||w||=1$, $\hat{\gamma}^{(i)} = \gamma^{(i)}$ 

>Max margin classifier:

Geometric margin $\gamma = \min_{i} \gamma^{(i)}$

Max margin classifier: $\max_{\gamma, w, b} \gamma$ s.t. $y^{(i)}(w^Tx^{(i)}+b)\geq \gamma$, $||w||=1$