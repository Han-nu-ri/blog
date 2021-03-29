# Regularization
Regularization은 머신러닝에서 굉장히 중요한 주제입니다. 
우리가 어떤 데이터에 대하여 모델을 fitting 시키는데, general한 trend에 fitting 시킬수록 좋습니다. Overfitting은 학습 데이터의 노이즈가 있을 때, 이 노이즈까지 fitting하는 것을 말합니다. 모델이 불필요하게 복잡하다면 Overfitting의 증거일 수 있습니다.

이것을 방지하기 위해 도입하는 개념이 Regularization입니다. 보통 목적 함수에 penalty항을 더하여, 모델이 불필요하게 복잡해지는 것을 막아줍니다.

### Ridge Regression
Linear Regression의 목적 함수에 계수의 제곱(Penalty term)을 더하여 Regularization하게 됩니다. 이 의미를 생각해보면, 계수가 원래의 목적 함수를 줄이는데 기여하지 않는다면 그 값을 쓸데 없이 높게 만들지 않는다는 것 입니다.
$$
\min_{\theta}(Y-X\theta)^T(Y-X\theta) + \lambda||\theta||_2^2
$$
### Lasso Regression
계수의 제곱이 아니라 절대값으로 둘 수 있습니다. 계수들이 sparse representation으로 되는 특징이 있습니다.
$$
\min_{\theta}(Y-X\theta)^T(Y-X\theta) + \lambda||\theta||_1
$$

## Regularization for Deep Neural Networks
딥러닝은 이 오버피팅에 굉장히 취약해서, Regularization이 중요합니다.
### Weight Decay
Ridge와 Lasso처럼 Weight의 2-norm과 1-norm을 목적 함수에 더해줍니다.
### Early Stopping
Validation set을 활용해서, validation loss가 커질 때 overffing 되고 있다고 판단하여 멈춥니다. 다만 기준은 어떤 데이터를 활용하여 어떤 문제를 다루느냐에 따라서 적절히 판단해주어야 합니다.
### Dropout
forward pass할 때 임의로 몇 뉴런들을 0으로 만듭니다. 얼마나 drop할 것인가는 hyperparameter로 정합니다.
뉴럴넷의 capacity가 크다면, 모델은 중복된 표현들을 가질 수 있습니다. 예를 들어 고양이를 인식할 때 고양이의 눈과 귀, 코의 representation들로 판단할 수 있습니다. 고양이의 눈을 주지 않아도, 학습이 잘 되어 있다면 귀와 코로 고양이임을 판단할 수 있겠죠. 이것이 Dropout의 intuition입니다.
layer 크기의 벡터를 랜덤함수로 채운 후에, drop out parameter 보다 작은 것들을 0으로 만들고 남은 값들을 drop out hyperparameter로 나눠서 scale을 맞춰줍니다.
### Stochastic Depth
Dropout과 비슷하게, 몇 가지 layer의 집합을 skip합니다.
### Cutout
Data augmentation과 비슷합니다. 훈련 이미지 안의 특정 영역을 임의로 골라서 0으로 만드는 것 입니다. 전처리가 들어가기 때문에 큰 데이터 셋에 대해서는 잘 쓰이지 않습니다.
### Regularization in Practice
dropout/batch normalization은 대부분 좋습니다. data augmentation과 early stopping은 잘 쓰면 좋습니다.

# Optimization beyond SGD
SGD를 쓸 경우, 가야 하는 방향 대로 가지 못하고 jittering하는 현상이 있습니다. 또한 gradient가 0인 경우 get stuck하기도 합니다.
SGD의 세 가지 문제점들은 아래와 같습니다.
1. Jittering
2. Local optimum
3. Inaccurate Gradient Estimation
데이터가 크다면 mini-batch를 활용하여 estimate된 gradient는 부정확할 수 있습니다. 예를 들어 데이터 셋이 수백만개이면 batch size가 수천개라도 그 비율은 굉장히 작습니다.

### SGD + Momentum
물리학에서 Momentum은 mass와 velocity의 곱입니다. 우리가 다루고자 하는 SGD에서 Momentum을 활용한 개념에서의 Momentum은 inertia(관성)에 더 가깝습니다.
즉 gradient가 줄어드는 방향이 있으면 그 관성을 다음 업데이트 때 반영해주는 것 입니다.
### AdaGrad
역사를 가지고, gradient가 컸던 방향이면 완만하게 가도록 하고 작았던 방향이면 더 가보도록 해주는 아이디어입니다.
### Leaky AdaGrad

<!--stackedit_data:
eyJoaXN0b3J5IjpbMzgyMTY5OTA2LC02MDYyMjY0NTMsLTg5Nj
MwNjc1Myw2NjM5NDgxNjIsMTI5NzI3NjY3LDEzNDk4MDUzNzMs
MTExMDczMzY2MiwxMTQ5NTIwNTg1LC0xNjU4MjcxMjcsOTM4ND
czMzA4XX0=
-->