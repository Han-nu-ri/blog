# Activation functions: Sigmoid, Tanh, ReLU
뉴럴 네트워크의 non-linearity 표현을 가능하게 해주는 activation function에 관한 포스트입니다. 서울대학교 이준석 교수님의 '시각적 이해를 위한 기계학습' 강의를 듣고 정리하였음을 밝힙니다.
## Sigmoid Function
Sigmoid fuction은 아래와 같은 식으로 정의 됩니다.
$$
\sigma(x)={1 \over 1+e^{-x}}
$$
![image](https://user-images.githubusercontent.com/11609881/112778853-6c2c7a80-9080-11eb-9af8-44d9b93ce0a6.png)
Sigmoid function의 장점은 0에서 1 사이의 값이 나온다는 것 입니다. 그렇기 때문에 사람이 값을 해석하기가 상대적으로 쉬워 역사적으로 유명합니다
<!--stackedit_data:
eyJoaXN0b3J5IjpbODQwMjY4NzM1XX0=
-->