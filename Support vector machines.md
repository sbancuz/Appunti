---
tags:
  - machine_learning
---
These are one of the best methods for [[Classification]]. Given a subset of training examples $x$, a vector of weights for them $a$ and a similarity function -- i.e. a [[Kernel methods]]. We can define a class prediction $x_{q} (t_{i}\in \{ -1,1 \})$ 
$$
f(x_{q}) = sign\left( \sum_{m \in S}\alpha_{m}t_{m}k(x_{q},x_{m}) + b \right)
$$
where $S$ is the set of **indices** of the support vector. 

>[!info]
>Support vectors are usually presented as a **generalization** of [[Perceptron]] in fact
>$$
> f(x_{q}) = sign \left( \sum w_{j}\phi_{j}(x_{q}) \right) \qquad w_{j} = \sum \alpha_{n}t_{n}\phi_{j}(x_{n}) \implies f(x_{q}) = sign\left( \sum \alpha_{n}t_n(\phi(x_{q}\phi(x_{n}))) \right) 
>$$

Now the problem is, how do i choose these weights? I want weights that maximize the margin that our classifier leaves for the data
$$
Margin =\min t_{n}(w^{T}\phi(x_{n}) + b)
$$
So the maximum solution is found by solving
$$
w^{*} = \arg\max\left( \frac{1}{||w||_{2}}  \min t_{n}(w^{T}\phi(x_{n}) + b)\right)
$$

>[!warning]
>This is not yet a kernel method, it's in fact a parametric one. We need to compute the dual

Here we have a **quadratic programming** problem, so a solution must lie in the subspace spanned by
$$
\{ \triangledown h_{i}(w^{*} : i = 1,2,\dots) \}
$$
This means that we can compute the [[Ottimizzazione per funzione di più variabili#Metodo dei moltiplicatori di Lagrange|Lagrangian function]] 
$$
L(w,\lambda) = f(w) + \sum\lambda_{i}h_{i}(w)
$$
and solve for $\triangledown L(w^{*},\lambda^{*}) = 0$

We also need to introduce another set of Lagrangian multipliers $\alpha_{i}$ since we have inequalities. To have an optimum of a function we need to have
$$
\begin{align}
\triangledown L(w^{*},\alpha^{*},\lambda^{*}) = 0  & \qquad h_{i}(w^{*}) = 0  & \qquad g_{i}(w^{*}) \leq 0 \\
\alpha_{i}^{*} \geq 0  & \qquad \alpha_{i}^{*}g_{i}(w^{*}) = 0
\end{align}
$$
So support vectors are the points where there are active constraints -- $g_{i}(w^{*}) = 0)$.

Now we need to compute the dual. Consider the Lagrangian
$$
L(w,b,\alpha) = \frac{1}{2}||w||_{2}^{2} - \sum\alpha_{n}(t_{n}(w^{T}\phi(x_{n}) + b) -1)
$$
and putting the gradient w.r.t $w$ and $b$ to zero we get
$$
w = \sum\alpha_{n}t_{n}\phi(x_{n}) \qquad \sum \alpha_{n}t_{n} = 0
$$
If we put the $w$ back in the first equation we get 
$$
\hat{L}(\alpha) = \sum\alpha_{n} - \frac{1}{2} \sum_{n}\sum_{m} \alpha_{n}\alpha_{m}t_{n}t_{m}k(x_{n},x_{m})
$$
and we want to maximize it with $\alpha_{n} \geq 0$ and $\sum\alpha_{n}t_{n} = 0$. So, to summarize the classification of the new points is given by
$$
y(x) = sign\left( \sum\alpha_{n}t_{n}k(x,x_{n}) + b \right) \qquad b = \frac{1}{N_{S}}\sum_{n}\left( t_{n} - \sum_{m}\alpha_{m}t_{m}k(x_{n},x_{m}) \right)
$$
>[!info]
>Notice that $N_{S} < N$ so they will be much faster!
### Noisy data

To handle noise in the data we can introduce slack variables $\xi_{i}$ that allow to violate the margin constraints, but at a cost. So now the problem becomes to minimize
$$
||w||_{2}^{2} + C\sum\xi_{i} \qquad t_{i}(w^{T}x_{i} + b) \geq 1 -\xi_{i} \qquad \xi_{i} \geq 0
$$