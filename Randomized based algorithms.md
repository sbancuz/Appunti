---
tags:
  - parallel_computing
---
[[Algorithms]] are deterministic, for a fixed input, it will run the same way every time. In a randomized algorithm this is not the case, the result may depend on a flip of a coin.

### Key analysis tool

Indicator variables $x_{i}$ that represents the individual elements of a random variable $x = \sum x_{i}$
### Las Vegas algorithm

The sorting algorithm always gives the correct solution, the only variation is the running time. It is done by running the algorithm multiple times with a different random input each time and returning only when it gives get a valid result.

The Las Vegas is efficient if on any input its expected running time is bounded by a  polynomial function of the input size.

![[Monte Carlo algorithm]]

![[Quicksort]]