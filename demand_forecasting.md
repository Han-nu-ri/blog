(a) Simple exponential smoothing,
$$
y_t=\alpha D_{t-1}+({1-\alpha}) y_{t-1}.
$$
with alpha=0.3.
$$
y_2=0.3D_1+0.7y_1=D_1=1000 \\
y_3=0.3D_2+0.7y_2=(0.3)*1113+0.7*1000 \\
\vdots \\
y_{12}=0.3D_{11}+0.7y_{11}\\
y_{13}=0.3D_{12}+0.7y_{12}\\
$$ 

(b) Double exponential smoothing,
$$
y_t=I_{t-1}+S_{t-1} \\
= \alpha D_{t-1}+(1-\alpha)(I_{t-2}+S_{t-2}) \\ + \beta (I_{t-1}-I_{t-2})+(1-\beta)S_{t-2}.
$$
with alpha=0.05, beta=0.1.
Initialization.
$$
y_1=I_1 = D_1=1000 \\
S_1=D_2-D_1. \\
$$
$$
y_2=I_1+S_1=D_1+(D_2-D_1)=D_2=1113 \\
y_3=I_2+S_2=(0.05)D_2+(0.95)(I_1+S_1) \\ + 0.1(I_2-I_1)+0.9S_1 \\
\vdots
$$

## Bass diffusion model
새로운 IT기기가 발매되면 바로 구매하시는 편이신가요? 저는 보통 사용 해본 사람들의 경험을 듣고 사는 편 인데, 이 글을 읽으시는 분들 중에는 얼리어댑터분들도 계시겠지요. 이렇게 얼리어댑터와 같은 Innovator들이 처음 제품을 사고, 그 소문이 저와 같은 Imitator들에게 확산되어 제품을 수요가 변하는 양상을 모델링한 것을 Bass diffusion model이라고 합니다.
Innovator들의 수요는 처음에 최고조로 시작하다가 점점 줄어들게 되고, Imitator들의 수요는 처음 없다가 점점 증가해서 최고점을 찍고 내려오게 됩니다. 아래 그림은 t 시간에 Innovator와 Imitator가 제품을 사는 경향을 보여줍니다.
![image](https://user-images.githubusercontent.com/11609881/111876772-a1cbc680-89e3-11eb-982f-f4776ab0c895.png)
이런 수요 모델을 '제품을 사지 않은 사람이 t 시간에 제품을 살 확률'로 수식적으로 표현하면 아래와 같습니다.
$$
P(t)=p+{q \over m}D(t),\\
P(t): \text{t시간에 제품을 살 확률} \\
p: \text{innovation 계수} \\
q: \text{imitation 계수} \\
m: \text{market 크기} \\
D(t): \text{t 시간 까지의 누적 수요}\\
$$

제품이 처음 시장에 나올 때 그 제품을 살 확률은 어떻게 될까요? t=0이므로, 누적 수요가 없어서 D(0)=0이 됩니다. 따라서 P(0)=p가 되지요. 즉 p는 Innovator에 의한 초기 수요를 '확률'로 표현한 계수입니다. 시간이 지날수록, Innovator에 의해 Imitator들이 수요 욕구가 감염되기 시작합니다. 이것은 t 시간까지의 누적 수요에 비례하여 D(t)*q/m으로 표현됩니다.

P(t)를 순간 수요와 누적 수요, 시장 크기로 나타낼 수 있습니다. 아직 사지 않은 잠재적 구매층의 크기는 '시장의 크기 - 누적 수요'로 나타낼 수 있고, 이 중 t 시간의 순간 구매층
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExODkwMDI4MCwyNDAyMTYwOV19
-->