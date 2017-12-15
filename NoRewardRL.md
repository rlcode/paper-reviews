### Curiosity-driven Exploration by Self-supervised Prediction

[Curiosity-driven Exploration by Self-supervised Prediction](https://pathak22.github.io/noreward-rl/resources/icml17.pdf)이란 논문이 있다. 여기서는 환경에서 리워드를 주지 않고 curiosity를 이용한 내부의 reward만 갖고 마리오와 둠을 학습시킨다. 보상이 자주 있지 않은 경우에 학습을 하면서 어려움이 생기는데 이 논문은 curiosity라는 새로운 보상을 이용해 문제를 해결한다.

* 현실 세계에서는 environment에서 주는 보상이 자주 있지 않다.(보통의 경우 보상이 sparse함) 이런 경우 policy를 업데이트 하는데 보상을 받을 때 만 policy를 업데이트 하게되는 문제가 있다. (보상이 주어지지 않을 때엔 크게 의미 없는 업데이트를 하게 된다.)    

* 인간의 경우는 보상이 자주 있지 않아도 curiosity가 새로운 스킬을 배우는 보상이 될 수 있다.     

* 이 논문에서는 curiosity가 내부의 보상을 만들어 주고 이 보상은 에이전트가 탐험을 하게 하거나 나중에 유용한 스킬을 배우도록 할 수 있다.  

* curiosity : 에이전트가 다음 상태를 예측하도록 하여 다음 상태를 잘 예측하지 못할 경우 높은 curiosity를 준다. 다음 스테이트를 잘 예측한다면 이미 가본 상태라고 판단 낮은 curiosity를 준다.  

* pixel을 이용해 학습을 할 때 한 상태의 pixel을 이용해 end-to-end로 다음 상태의 pixel을 예측 하는 것은 어려움이 있다. 따라서 상태의 feature space를 이용해 feature를 예측하게 한다.

<br>

![curiosity driven algorithm](/assets/curiosity_driven.png)

* $s_t$, $a_t$, $s_{t+1}$이 ICM(Intrinsic Curiosity Module)에 들어가면 ICM이 intrinsic reward(curiosity)를 내뱉어 준다.  

* $s_t$, $s_{t+1}$은 각각 network를 통과해 feature space($\phi(s_t)$, $\phi(s_{t+1})$)로 변환된다.  

* $\phi(s_t)$, $a_t$는 forward model을 통해 $\phi(s_{t+1})$을 예측하도록 학습한다. 상태의 feature space 학습에는 MSE error를 이용한다.  

  $L_F(\phi(s_t), \phi(s_{t+1})) = {1\over2}\lvert \hat{\phi}(s_{t+1})- \phi(s_{t+1})\rvert^2$

* intrinsic reward로 $r_t^i = {\eta\over2}\lvert\hat\phi(s_{t+1})-\phi(s_{t+1})\rvert^2$을 준다. Policy를 학습을 할 때는 환경에서 주는 reward와 더해서 $r_t^i + r_t^e$을 reward로 준다.  

* $\phi(s_t)$,  $\phi(s_{t+1})$는 inverse model을 통해 $a_t$를 예측하도록 학습한다. inverse model을 학습시키는 것은 feature를 학습시키는데 도움을 준다고 한다.  

* action space가 discrete 한 경우에는 inverse model의 output은 softmax이고 cross-entropy로스를 이용한다.  

* policy gradient 로스까지 더한 최종 로스는 다음과 같다.  

  $min_{\theta_P, \theta_I, \theta_F }[-\lambda E_{\pi(s_t;\theta_P)}[\Sigma_t r_t] + (1-\beta)L_I + \beta L_F]$

   ($\beta$는 0~1사이의 스칼라 값으로 논문에서는 0.2를 이용한다.)

* 환경에서 주는 보상 없이 curiosity만 이용해서 학습을 해도 학습이 된다고 한다. 논문에서는 환경에서 주는 보상 없이 마리오와 둠을 학습시켰다고 한다.  

