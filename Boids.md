---
tags:
  - AI
---
**Boids** is an artificial life program, developed by [Craig Reynolds](https://en.wikipedia.org/wiki/Craig_Reynolds_(computer_graphics) "Craig Reynolds (computer graphics)") in 1986, which simulates the flocking behaviour of birds. The name "boid" corresponds to a shortened version of "bird-oid object", which refers to a bird-like object.

Rules applied in simple Boids
As with most artificial life simulations, Boids is an example of emergent behavior; that is, the complexity of Boids arises from the interaction of individual agents (the boids, in this case) adhering to a set of simple rules. The rules applied in the simplest Boids world are as follows:
- **separation**: steer to avoid crowding local flock mates
- **alignment**: steer towards the average heading of local flock mates
- **cohesion**: steer to move towards the average position (center of mass) of local flock mates
