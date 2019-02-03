---
layout: default
mathjax: true
---
<p class='message'>
1) How does the $\frac{1}{2}$ in $ J(\theta) = min_{\theta}\frac{1}{2}\sum_{i=1}^{m}(h_{\theta}(x^{(i)}) - y^{(i)})^{2}$ affect the final result, since we put it there just to "make our calculations easier"?
</p>
Since later on we introduce $\alpha$ (which we choose whatever we want), we can observe that $\alpha_{1} = \alpha \frac{1}{2}$ 

----- 
<p class='message'>
2) What is the square error method?
</p>
<img align="right" src="/CS/public/line-fit-errors.png" height="200" width="200"> We're trying to minimize the blue distances by shifting and rotating the red line. Suppose the line is of form $y=mx+b$ and points are $(x_{i}, y_{i})$, then $\sum_{i}^{m}|mx+b - y_{i}|$ is what we're to minimize. But we don't do absolute value(see question 3), instead we raise it to the power of 2

-----
<p class='message'>
3) Why not other methods like absolute value, or minimize the perpendicular distances from point to line?
</p>
Absolute values are a pain. My guess is that's why we don't deal with them. Also, the method of minimizing the perpendicular distances: 
$\frac{|Am+Bn+C|}{\sqrt{A^{2}+B^{2}}}$ is a formula of such a distance, where $Ax+By+C=0$ is a line and $(m,n)$ is a point.

Do you know how to differentiate it with the respect to $\theta$? I don't, so that's why I won't use it personally :)

-----
<p class='message'>
4) Why do we have minus sign in this one: $ \theta_{i} := \theta_{i} - \alpha\frac{\partial}{\partial\theta_{i}}J(\theta)$?
</p>
<img align="right" src="/CS/public/parabola5.png" height="200" width="200">
Let's make this formula simples by reducing our training examples to one and making $J(\theta)=\theta^{2}$, so we have $ \theta := \theta - \alpha\frac{\partial}{\partial\theta}\theta^{2}$. Suppose that the $\theta$ is as on the picture. Therefore we have derivative $> 0$ so we will have $\theta$ minus something, which will lead us to the local minima

-----
<p class='message'>
5) Why we $J(\theta)$ is always convex?
</p>
$ 2J(\theta) = \sum_{i=1}^{m}(h_{\theta}(x^{(i)}) - y^{(i)})^{2} = \sum_{i=1}^{m}((\theta_{0} + \theta_{1}x^{(i)}) - y^{(i)})^{2} = \\\\ 
\sum_{i=1}^{m}(\theta_{0}^{2} + \theta_{1}^{2}(x^{(i)})^{2} + (y^{(i)})^{2} - 2\theta_{0}\theta_{1}x^{(i)} - 2\theta_{0}y^{(i)} - 2\theta_{1}x^{(i)}y^{(i)}) $ 

Now we can observe that our equation above and the $f(x,y) = ax^2 + by^2 - cxy - dx - ry + m$ are identical. Also we know that $f(x,y)$ is convex, therefore $2J(\theta)$ is also convex

<p class='message'>
6) Why MSE may be a bad choice?
</p>

There is no guarantee that the method with the lowest training MSE will also have the lowest test MSE