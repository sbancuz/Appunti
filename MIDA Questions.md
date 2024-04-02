---
tags:
  - mida
---
---
### Being as rigorous as possible, explain what is going on in PEM identification when the number of data points N grows unbounded. In particular explain what happens to $J_{N}(\theta)$ and its minimizer. Explain also the significance of this result in the case that $\exists {\theta_{0}} : \mathcal M(\theta_{0}) = \mathcal S {}$ 

PEM are a family of methods that are used to find the bast parameters $\theta$ for a model. The basic idea is to define a cost function $J_{N} = \frac{1}{N}\sum \epsilon(t;\theta)^{2}$ that represents the mean of the error of our predictor given by the data. In fact $\epsilon(t;\theta) = y(t) - \hat{y}(t|t-1; \theta)$. When $N$ grows unbound it means that we have an infinite number of points from which to derive our predictor, and as such the error should tend to 0. 