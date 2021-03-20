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
새로운 IT기기가 발매되면 바로 구매하시는 편이신가요? 저는 보통 사용 해본 사람들의 경험을 듣고 사는 편 인데, 이 글을 읽으시는 분들 중에는 얼리어댑터분들도 계시겠지요.
이렇게 제품의 수요를 얼리어댑터와 같은 Inno구매해Bass diffusion model은
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2OTIwOTQ2NjMsLTc3NzkyNDgwNyw5MT
Y3MjY0NTgsLTExMjc5MDM5NzIsMzEzMjgwOTk3LDczMDk5ODEx
Nl19
-->