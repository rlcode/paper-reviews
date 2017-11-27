# Deterministic Policy Gradient Algorithms

[`link`](http://proceedings.mlr.press/v32/silver14.pdf)

This paper is about 'deterministic policy gradient algorithms'

1. deterministic policy gradient consider reinforcement learning with continuous actions.
2. to ensure adequate exploration, DPG use off-policy actor-critic algorithm.
3. Determinisitc policy  ![equation](https://latex.codecogs.com/gif.latex?a%20%3D%20%5Cmu_%5Ctheta%20%28s%29)
4. computing  the stochastic policy gradient may require more samples than computing DPG, especially if the action space has many dimensions.
