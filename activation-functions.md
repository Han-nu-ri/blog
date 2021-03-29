# Activation functions: Sigmoid, Tanh, ReLU
뉴럴 네트워크의 non-linearity 표현을 가능하게 해주는 activation function에 관한 포스트입니다. 서울대학교 이준석 교수님의 '시각적 이해를 위한 기계학습' 강의를 듣고 정리하였음을 밝힙니다.
## Sigmoid Function
Sigmoid fuction은 아래와 같은 식으로 정의 됩니다.
$$
\sigma(x)={1 \over 1+e^{-x}}
$$
![image](https://user-images.githubusercontent.com/11609881/112778853-6c2c7a80-9080-11eb-9af8-44d9b93ce0a6.png)
Sigmoid function의 장점은 0에서 1 사이의 값이 나온다는 것 입니다. 그렇기 때문에 사람이 값을 해석하기가 상대적으로 쉬워 역사적으로 유명합니다.
Sigmoid function의 단점은 세 가지가 있습니다.
1. zero-centered 되어 있지 않습니다.
zero-centered 되어 있지 않다면 어떤 문제가 발생할까요? 우리의 데이터가 모두 양수라고 해보죠. WX+b가 sigmoid의 입력으로 들어가는 경우, 우리는 local gradient인
$$
{\partial \sigma(W^TX+b) \over \partial W_i}=\sigma(W^TX+b)(1-\sigma(W^TX+b)X_i
$$
를 구해야 합니다. 식을 살펴보면 3가지 요소가 모두 양수임을 알 수 있습니다. 따라서 gradient는 계속 한 방향으로만 업데이트가 됨을 알 수 있습니다.
2. exp 연산이 computationally expensive합니다.
3. gradient가 vanishing합니다.
sigmoid function을 미분하게 되면
$$
{\partial \sigma(x) \over \partial x} = \sigma(x) (1-\sigma x)
$$
과 같습니다. 따라서 x의 절대값이 커지게 되면 미분이 0에 가까워지기 때문에 gradient가 vanishing하는 문제가 있습니다.
## Tanh
tanh는 어떨까요? zero-centered이고, 출력의 범위는 [-1, 1]입니다.
![image](https://user-images.githubusercontent.com/11609881/112780051-f83fa180-9082-11eb-8975-f9c17efd202d.png)
하지만 tanh은 sigmoid function의 scaled 버전에 불과합니다.
$$
tanh(x)=2\sigma(2x)-1
$$
따라서 sigmoid function에 있는 gradient vanishing 문제가 여전히 있습니다.
## ReLU
ReLU(Rectified Linear Unit)은 max(0, x)과 같은 식으로 표현됩니다. + region에서 값이 saturate하지 않고, computationally efficient하며 sigmoid/tanh 보다 더 빨리 수렴하는 장점을 가지고 있습니다.
![image](https://user-images.githubusercontent.com/11609881/112780508-f5917c00-9083-11eb-8846-d8a0a13582cf.png)
ReLU에도 단점들이 존재합니다.
1. 출력이 Zero-centered 되어 있지 않습니다.
2. x=0 부분에서 미분 가능하지 않습니다.
3. Dead ReLU Problem이 있습니다.
ReLU의 입력(WX+b)으로 음수가 들어오게 되면, backpropagation시 음수인 곳에는 gradient가 흘러 들어가지 않습니다. 따라서 업데이트가 되지 않는 문제가 있습니다.

위 단점들 중 3번을 개선하기 위해 Leak ReLU가 제안되었습니다. Leak ReLU는
max(0.01x, x)와 같이 x가 음수인 곳을 0으로 만들지 않고, slope를 곱해서 느리게 증가하도록 하였습니다. 당연히 값이 존재하므로 Dead ReLU Problem이 발생하지 않음을 이해할 수 있습니다.
$$
max(slope*x, x)
$$
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NzA4OTQ2NjUsLTIxNDY4NTQ5NDMsLT
E5OTk4MDc2NTQsLTE5NDkyNzc5NjcsLTgxOTIxMTI0NSwxODY1
OTE1NDY2XX0=
-->