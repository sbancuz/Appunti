---
tags:
  - security
---
A communication takes place between two endpoints, a sender and a receiver. Information, that can generally be seen as even a random variable, is carried by a channel in the form of a sequence of symbols of a **finite alphabet**.

>[!note]
>A finite alphabet means that each symbol can carry at most some amount of information

The receiver can get information only through a channel, the information is **uncertain** -- measured with [[Entropy]] -- on what the next symbol that is going to arrive, until it arrives. Thus the sender can be modeled to send a [[Probability theory#Random variables]]. Acquiring information means to reduce the amount of uncertainty of a random variable. So
- The amount of information depends on the distribution $\mathcal X$
- the closer is $\mathcal X$ to a uniform distribution, the higher the amount of information I get from knowing an outcome

It's possible to encode the outcomes $n$ of a [[Probability theory#Random variables]], each one with [[Entropy]] $H(\mathcal X)$ into no less than $nH(\mathcal X)$ bits per outcome.
