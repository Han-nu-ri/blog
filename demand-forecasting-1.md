# demand-forecasting-1: Bass diffusion model
수요 예측 모델 중 Bass diffusion model에 관한 포스트입니다. 서울대 박건수 교수님의 생산계획 및 통제 강의와 Fundamentals of Supply Chain Theory, 2nd Edition를 참고하여 정리했음을 밝힙니다. 

## Bass diffusion model
새로운 IT기기가 발매되면 바로 구매하시는 편이신가요? 저는 보통 사용 해본 사람들의 경험을 듣고 사는 편 인데, 이 글을 읽으시는 분들 중에는 얼리어댑터분들도 계시겠지요. 이렇게 얼리어댑터와 같은 Innovator들이 처음 제품을 사고, 그 소문이 저와 같은 Imitator들에게 확산되어 제품을 수요가 변하는 양상을 모델링한 것을 Bass diffusion model이라고 합니다.
Innovator들의 수요는 처음에 최고조로 시작하다가 점점 줄어들게 되고, Imitator들의 수요는 처음 없다가 점점 증가해서 최고점을 찍고 내려오게 됩니다. 아래 그림은 t 시간에 Innovator와 Imitator가 제품을 사는 경향을 보여줍니다.
![image](https://user-images.githubusercontent.com/11609881/111876772-a1cbc680-89e3-11eb-982f-f4776ab0c895.png)
이런 수요 모델을 '제품을 사지 않은 사람이 t 시간에 제품을 살 확률'로 수식적으로 표현하면 아래와 같습니다.
$$
P(t)=p+{q \over m}D(t),
P(t): \text{t시간에 제품을 살 확률} 
$$
$$
p: \text{innovation 계수},
q: \text{imitation 계수},
m: \text{market 크기}, 
D(t): \text{t 시간 까지의 누적 수요}
$$

제품이 처음 시장에 나올 때 그 제품을 살 확률은 어떻게 될까요? t=0이므로, 누적 수요가 없어서 D(0)=0이 됩니다. 따라서 P(0)=p가 되지요. 즉 p는 Innovator에 의한 초기 수요를 '확률'로 표현한 계수입니다. 시간이 지날수록, Innovator에 의해 Imitator들이 수요 욕구가 감염되기 시작합니다. 이것은 t 시간까지의 누적 수요에 비례하여 D(t)*q/m으로 표현됩니다.

P(t)를 순간 수요와 누적 수요, 시장 크기로 나타낼 수 있습니다. 예를 들어 10명 중 t 시간까지 직전까지 구매한 사람이 5명이라고 하고, t 시간에 구매한 사람을 2명이라고 해보죠. 그럼 P(t)를 2 / (10 - 5)으로 표현할 수 있습니다.
다시 말해  P(t)는 아직 사지 않은 잠재적 구매층의 크기 ('시장의 크기 - 누적 수요') 중  t 시간 순간에 구매한 크기의 비율이 됩니다.
$$
P(t) = {d(t) \over m-D(t)}
$$
이를 이산 시간의 Bass model이긴 하지만, 베이즈룰을 활용하면 쉽게 유도할 수 있습니다. A를 t 시간의 구매하는 사건, B를 t 시간 전에 구매하지 않을 사건이라고 하면 P(t)=P(A|B)입니다. 베이즈룰 통해 전개해보면,
$$
P(A|B)={P(B|A)P(A) \over P(B)} \\
$$
입니다.
P(B|A)는 t 시간에 구매한 사건이 주어졌을 때 t 시간 전에 구매하지 않을 확률이므로 당연히 1이 됩니다. P(A)는 t 시간에 구매할 확률이므로 d(t)/m이 됩니다. P(B)는 t 시간 전에 구매하지 않을 확률이므로, '1 - t 시간 전까지 구매할 확률'이므로 '1-D(t)/m'입니다. 따라서,
$$
P(A|B)={P(B|A)P(A) \over P(B)}
={1 \times {d_t \over m} \over {1-{D(t) \over m}}}
= {d_t \over m-D(t)}
$$
입니다.

위 식을 만족하는 closed-form의 표현은 아래와 같습니다. (증명은 생략합니다)
$$
D(t)=m{1-e^{-(p+q)t} \over {1+{q \over p}e^{-(p+q)t}}}, 
d(t)={{mp(p+q)^2e^{-(p+q)t}} \over (p+qe^{-(p+q)t})^2}
$$

d(t)를 t에 대해서 미분하여 0인 지점을 확인하면 수요가 정점을 찍는 순간(t*)과 그때의 수요, 누적 수요를 알 수 있습니다.
$$
t^{\ast}={1 \over p+q}ln({q \over p}), 
d(t^{\ast})={m(p+q)^2 \over 4q}, 
D(t^{\ast})={m(q-p) \over 2q}
$$

  

p:0.07, q: 0.31, m: 170000일 때, 누적 수요가 전체 market size의 90%가 되는 시점은 언제를 구해보죠.
$$
{D(t) \over m} = 0.9 
={1-e^{-0.38t} \over 1+{0.31 \over 0.07}e^{-0.38t}} 
$$
$$
0.1=(1+{0.9 \times 0.31 \over 0.07})e^{-0.38t} , 
e^{0.38t}= 10 + {9 \times 31 \over 7}, 
e^{0.38t}= {70 + 9 \times 31 \over 7}
$$
$$
e^{0.38t}= {349 \over 7}, 
t = {ln({349 \over 7}) \over 0.38} = 10.28726782\\
$$
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTcwODIyNjUwMiwxMzA1Nzg3Mzg0LDg2Nz
g0MzE0MCw4NzcxMjU3MTIsLTE4NDA5Nzc5MzEsMTY4OTgyMTA2
MywtMTQyMjMxNDE4LDIxMjA2Mzg1NTJdfQ==
-->