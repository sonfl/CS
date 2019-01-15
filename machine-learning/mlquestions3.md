---
layout: default
mathjax: true
---
<p class='message'>
Why do we need weighted linear regression?
</p>
You must have heard about underfitting and overfitting. As Andrew describes it, it's a bad idea to used too much parameters (and too few also). WLR proposes another way to look at the problem by adding the $w^{(i)}$ function, which will yield ~1 when $|x^{(i)}-x|$ is small and ~0 when $|x^{(i)}-x|$ is big.

-----

<p class='message'>
Why do we initially maximize $L(\theta)$ but then transform into $l(\theta)=logL(\theta)$ and don't reverse back?
</p>
Because we minimize the parameter $\theta$. The maximum value for $L(\theta)$ and $l(\theta)$ will differ indeed. But since log is a strictly increasing function, the $\theta$ itself will be the same for both functions.