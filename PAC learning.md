---
tags:
  - machine_learning
---
Given a set of instances $X$, a set of hypotheses $H$ and a set of boolean functions that define the target concepts $C$. Additionally we also have training instances generated by a fixed, unknown probability distribution $\mathcal P$ over $X$. Our goal is to have a learner that can explain our training data $\mathcal D$. We start by defining the true loss function
$$
L_{true} = Pr_{x \in \mathcal P}[c(x) \neq h(x)]
$$
We want to **bound** $L_{true}$ given $L_{test}$. We first try to look at version spaces -- the space inside the hypothesis space where the training error is $0$.

![[Version space.png]]

If the hypothesis $H$ is **finite** and $\mathcal D$ is a sequence of $N\geq 1$ independent random examples of some target concept $C$, then for any $0\leq\epsilon\leq 1$, the probability that $VS_{H,\mathcal D}$ contains a hypothesis error greater then $\epsilon$ is less than $|H|e^{-\epsilon N} \leq \delta$

If we now pick $\epsilon,\delta$ we can compute how many samples do we need to have this kind of error
$$
N\geq \frac{1}{\epsilon}\left( \ln|H| + \ln \left( \frac{1}{\delta} \right) \right)
$$
>[!note]
>$\epsilon$ represents the accuracy, so the error i can tolerate and $\delta$ is the probability of having an error larger than what I can tolerate

We can define that $C$ is **PAC-learnable** if there exists and algorithm $L$ such that for every $f\in C$, for any distribution $\mathcal P$, for any $\epsilon,\delta$ such that $0\leq\epsilon,\delta<1/2$. The $L$, with probability $1-\delta$, outputs a concept $h$ such that $L_{true}(h)\leq\epsilon$ using a number of samples that is polynomial of $1/\epsilon$ and $1/\delta$

We can say that is also **efficiently PAC-learnable** iff for all $c\in C$, it's also **polynomial** in $M$ and $size(c)$.

But can we also extend this concept to non $0$ training errors? Yes, we just need to bound the gap
$$
L_{true}(h) \leq L_{train}(h) + \epsilon
$$and using the **Hoeffding bound** -- $Pr(\mathbb E[\bar{x}] - \bar{x}>\epsilon) , e^{-2N\epsilon^{2}}$ where $\bar{x}$ is the mean -- we can extend the definition to any learner
$$
Pr(\exists h\in H|L_{true}(h) - L_{train}(h) > \epsilon) \leq |H|e^{-2N\epsilon^{2}}
$$
This all means that 
$$
L_{true} (h) \leq L_{train}(h) + \sqrt{ \frac{\ln|H| + \ln \frac{1}{\delta}}{2N} }
$$
										^^ *bias*                        ^^ *variance*
So given $\delta,\epsilon$ 
$$
N \geq \frac{1}{2\epsilon^{2}}\left( \ln|H| + \ln \frac{1}{\delta} \right)
$$
This has a particularly bad implication, if $|H|$ infinite then the variance must be very high. This however is not entirely the case so we need another criteria that defines the quality of the hypothesis.
### VC-dimensions

A set of instances $S$ is **shattered** by an hypothesis space $H$ iff for every **dichotomy** -- a set $S$ is a partition of $S$ into two disjoint subsets -- there exists some hypothesis $H$ consistent with this dichotomy.

The **Bapnik-Chervonenkis dimension** of hypothesis space $H$ defined over instance space $X$ is the size of the largest finite subset of $X$ shattered by $H$. If arbitrarily large finite sets of $X$ can be shattered by $H$, then $VC(H)\equiv \infty$

So now 
$$
N\geq \frac{1}{\epsilon}\left( 4\log_{2}\left( \frac{2}{\delta} + 8 VC(H)\log_{2}\left( \frac{13}{\epsilon} \right) \right) \right)
$$

The VC dimensions of a hypothesis space $|H|<\infty$ is bounded by $\log_{2}(|H|)$ and if $VC(C)=\infty$ then $C$ is not PAC learnable.

>[!warning]
>This does not mean that they are impossible to learn, they are just very very hard!
