# Trust Region Policy Optimization

[`link`](https://arxiv.org/pdf/1502.05477.pdf)

## 1.	Stochastic policy gradient의 문제
* Sample efficiency is poor
* Policy gradient가 현재 policy에 대한 estimate
* Estimate한 policy gradient로 한 번만 update
* 이전 policy로 얻은 data를 사용하기 어려움
* Policy gradient는 parameter에서 step
* 따라서 parameter에서의 small step이 policy를 크게 변화시킬 수 있음 
* Policy가 조금씩 변하게 하는 step size를 찾기 어렵다

## 2.	따라서 Performance의 improvement를 보장하면서 학습하고 싶다
* Policy space에서 조금씩 움직이겠다 (new policy와 old policy 사이의 kl-divergence)
* Policy가 조금 변할 때 performance의 차이를 정의 : lower bound</br>
--> policy가 조금 변한다는 가정하에 local approximation을 정의</br>
--> local approximation으로 인한 오차를 lower bound로 정의</br>
--> lower bound를 optimize (2002 Kakade)</br>
* 	Penalty 문제를 constraint 문제로 바꿈 </br>
--> new policy와 old policy 사이의 kl-divergence가 constraint, 즉 policy가 일정 이상 못 변하게 하는 것</br> 
--> Trust Region method</br>
* Objective function은 1차 approximation, KL-divergence는 2차 approximation
* 극값을 통해 우선 direction을 구하고 step_size를 구한다
*	이 때 step_size를 line back tracking 알고리즘을 사용한다
