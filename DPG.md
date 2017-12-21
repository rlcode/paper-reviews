# Deterministic Policy Gradient Algorithms

[`link`](http://proceedings.mlr.press/v32/silver14.pdf)

이 논문은 'deterministic policy gradient algorithm'에 관한 논문입니다.

1. Deterministic policy gradient는 컨티뉴어스한 환경의 강화학습을 위해 고안되었음.
2. Stochastic policy gradient하고는 다르게 deterministic policy gradient는 exploration의 단점을 보완하기 위해 off-policy actor critic을 사용함.
3. Determinisitc policy  ![equation](https://latex.codecogs.com/gif.latex?a%20%3D%20%5Cmu_%5Ctheta%20%28s%29)
4. Stochastic policy gradient는 action spaces와 state spaces를 통합하였지만, determinisitc policy gradient 같은 경우에는 state spaces 만 통합함.
5. 큰 차원의 action space에 대해서 stochastic policy gradient를 계산하는 것은 deterministic policy gradient를 계산하는 것보다 더 많은 양의 계산이 필요함.
6. 한 번에 Q값을 미분하는 것이 아니고, Q값과 mu를 따로 미분하여 곱해주는 모양으로 바꿔 계산함.
7. Deterministic Policy Gradient Theorem은 기존의 서튼 교수의 Policy Gradient Theorem이랑 거의 비슷하게 증명함.
8. Stochastic off-policy actor-critic 알고리즘을 사용하기 때문에, actor와 critic 모두 Importance Sampling을 사용해야함. 하지만 deterministic policy gradient같은 경우에는 action을 통합하는 것이 없어졌기 때문에 actor에서 Importance Sampling을 피할 수 있음. 또한 critic에서는 Q-learning을 사용하므로써 Importance sampling을 피함.