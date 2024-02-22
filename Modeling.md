---
tags:
  - mida
---
The first thing to do when resolving a problem is to express that same problem as a **model**. A model can be used to further our understanding of a problem, to make prediction, simulate, design control systems or for fault detection. 
```math
||{"id":264570592324}||



```
But how do we build a [[System]]? 
### White box modeling

This is the process of constructing a model based from the physical laws or principles that govern the system, and as such the resulting model can be very **generalized**. This is not necessarily the best approach for modeling a problem since the system can be extremely **complicated** or there are too many moving parts or the computation is just too expensive.
### Black box modeling

In contrast this approach is based on data, the only things that affect the behavior is the **experimental data**. This makes developing a system extremely **simple** since we don't need to understand the behavior of the system. The only problem is that the resulting model won't be generalized, in fact it will be specific only to this problem.

>[!warning]
>The model will only be as good as the data from which it's created, if in the data we don't see some behavior, it won't ever be represented in the final model

This can be done with [[Machine learning]], especially with [[Machine learning#Supervised learning]].
### Gray box modeling

This is an hybrid approach that integrates missing knowledge, or difficult computation from the physical model with an estimation given by a black box model.
### Quality of the model

The output of the model will never exactly output the actual correct output of the model.
```math
||{"id":1680994712841}||


```
When we can't find no pattern in the data we call the data **[[white noise]]**. We can say that a model is good when there is no more pattern to extrapolate from the data. 
$$
\begin{align}
\epsilon(t)  & = y(t) - \hat{y}(t) \\
\hat{y}(t)  & = y(t) - \epsilon(t) \\
\hat{\hat{y}}(t)  & = \hat{y}(t) + \dot{\epsilon}
\end{align}
$$
