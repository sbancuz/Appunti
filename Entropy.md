---
tags:
  - security
---
This is a measure of **uncertainty**. Let $\mathcal X$ be a discrete [[Probability theory#Random variables]] with $n$ outcomes in $\{ x_{0},\dots,x_{n} \}$ with $Pr(\mathcal X=x_{i}) =p_{i}$ for all $0 \leq i\leq n$

The entropy of $\mathcal X$ is $H(\mathcal X) = \sum-p_{i}\log_{b}(p_{i})$

>[!note]
>The typical case of a base is 2

We define the **min-entropy** if $\mathcal X$ as $H_{\infty}(\mathcal X)=-\log(\max p_i)$. Guessing the most common bit outcome of $\mathcal X$ is at least as hard as guessing the min-entropy.
