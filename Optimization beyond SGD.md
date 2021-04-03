# Optimization beyond SGD
Mini batch로 Gradient를 Estimate하는 Stochastic Gradient Descent(SGD)은 Full batch로 Gradient Descent를 쓸 때보다 계산량이 줄어 속도가 빠르다는 장점이 있습니다. 하지만 SGD에는 아래와 같은 문제가 있어서, SGD를 개량한 Optimizer가 계속 제안되어왔습니다.
1. Jittering
서울에서 부산으로 가는데 
2. Local optimum
3. Inaccurate Gradient Estimation
데이터가 크다면 mini-batch를 활용하여 estimate된 gradient는 부정확할 수 있습니다. 예를 들어 데이터 셋이 수백만개이면 batch size가 수천개라도 그 비율은 굉장히 작습니다.

### SGD + Momentum
물리학에서 Momentum은 mass와 velocity의 곱입니다. 우리가 다루고자 하는 SGD에서 Momentum을 활용한 개념에서의 Momentum은 inertia(관성)에 더 가깝습니다.
즉 gradient가 줄어드는 방향이 있으면 그 관성을 다음 업데이트 때 반영해주는 것 입니다.
### AdaGrad
역사를 가지고, gradient가 컸던 방향이면 완만하게 가도록 하고 작았던 방향이면 더 가보도록 해주는 아이디어입니다.
### RMSProp: Leaky AdaGrad
AdaGrad의 divider에는 squared gradient가 누적되어 들어가기 때문에 learning rate이 빨리 떨어집니다.
### Adam
Momentum과 AdaGrad를 적절히 합친 optimizer입니다.

### First vs. Second-order Optimization
Second-order optimization을 하게 되면 횟수를 기준으로 더 빠른 convergence를 하게 됩니다. 그럼에도 Second-order를 쓰지 않는 이유는 Hessian size가 O(N^2)이고, 이를 Inverse하면 O(N^3)이 됩니다. 그래서 N이 굉장히 커지게 되면 더 오래 걸리므로 First-order Optimization을 대부분 씁니다.
### Optimizers in Practice
Adam으로 시작하고, SGD + Momemtum을 가끔 활용하기도 합니다. Learning rate을 잘 조절하는게 중요합니다.
### Learning Rate 조절하기
Learning rate을 너무 높게 주면 아예 loss가 발산하게 됩니다. 적절하게 세팅하는 것이 중요한데, initial learning rate을 크게 주고 점점 감소 시키는 것이 일반적입니다. 가진 데이터와 문제에 따라 learning rate을 잘 디자인하는 것이 필요합니다.

# Batch Normalization
데이터를 평균으로 빼고 표준편차로 나눠주는 Normalization을 Batch별로 하는 것을 Batch Normalization이라고 합니다.
### 테스트
테스트 시에는 훈련 데이터의 평균과 표준편차를 활용하여 Normalization해줍니다.
### 장점
딥네트워크를 훈련하기 쉬워지고
### 단점
테스트 시 훈련 데이터의 평균과 표준편차를 활용하여 Normalization할 때에는, 데이터들이 i.i.d임을 가정한 것 입니다. 하지만 시간이 흘러 실제 application의  데이터 셋이 많이 변경된 경우 i.i.d 가정에 맞지 않게 됩니다. 하여 한번 더 normalization 해주는 개념이 'Batch Renormalization입니다.
### 구현
실제 구현 시에는 FC layer와 Activation layer 사이에 Batch Normalization을 넣어줍니다. 왜냐면 Activation function에 0 주변의 값이 들어오게 되면 이점이 많기 때문입니다. 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyOTIxMzc5NTQsNTQ0MTYwMDAzXX0=
-->