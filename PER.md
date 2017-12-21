# Prioritized Experience Replay

[`link`](https://arxiv.org/abs/1511.05952)

이 논문은 'Prioritized Experience Replay'에 대한 논문입니다. (이하 PER)

1. PER은 중요한 transition을 더 자주 샘플링하고 더 효율적으로 학습하기 위한 Replay memory 알고리즘임.
2. Experience replay는 transition간의 상관관계를 깨주고, 희귀한 경험들을 한 번 이상 사용할 수 있게 해줌.
3. TD-error는 우선순위를 측정하는 한 가지 방법을 제공함.
4. 더 큰 TD-error를 가지는 transition은 네트워크 업데이트에 있어서 더 'surprising'하고 예상 불가능한 transition임.
5. PER을 구현하는 방법은 Ranked-base와 Stochastic-base가 있음.
6. Ranked-base는 전체 Replay memory에 대한 sweep을 피하기 위해서, 실제로 샘플링 되는 transition에 대해서만 TD-error가 업데이트 됨. 그 결과 TD-error가 낮아진다면 다시 샘플링되지 않을 수 있음. 또한 stochastic한 reward(noise spike)에 대해서도 민감함. 그 결과, 이 방법은 적은 샘플에 대해서만 초점이 잡혀있고 오버피팅이 될 문제가 있음.
7. Ranked-base의 문제를 해결하기 위해서 Sumtree라는 이진트리 구조를 이용하여 transition을 저장하고 샘플링함.
8. PER은 통제되지 않는 방법으로 expected value의 분포를 변경하기 때문에 Bias가 생김.
9. 이 Bias를 조절해주기 위해서 Importance-sampling weights를 사용함.
