# Regularization for neural networks
Regularization은 머신러닝에서 굉장히 중요한 주제입니다. 먼저 간단히 선형 회귀에서 활용되는 Regularization 기법에 대해서, 그리고 Neural Network에서 사용되는 기법들에 대해서 적어보려고 합니다. 서울대학교 이준석 교수님의 '시각적 이해를 위한 기계학습' 와 위키피디아를 참고했음을 밝힙니다.

우리가 어떤 데이터에 대하여 모델을 fitting 시키는데, general한 trend에 fitting 시킬수록 좋습니다. Overfitting은 학습 데이터의 노이즈가 있을 때, 이 노이즈까지 fitting하는 것을 말합니다. 만약 모델이 불필요하게 복잡하다면 Overfitting의 증거일 수 있습니다.

이것을 방지하기 위해 도입하는 개념이 Regularization입니다. 보통 목적 함수에 penalty항을 더하여, 모델이 불필요하게 복잡해지는 것을 막아줍니다.

## Regularization for Regression
### Ridge Regression
Linear Regression의 목적 함수에 계수의 제곱(Penalty term)을 더하여 Regularization하게 됩니다. 이 의미를 생각해보면, 계수가 원래의 목적 함수를 줄이는데 기여하지 않는다면 그 값을 쓸데 없이 높게 만들지 않는다는 것 입니다.
$$
\min_{\theta}(Y-X\theta)^T(Y-X\theta) + \lambda||\theta||_2^2
$$
### Lasso Regression
계수의 제곱이 아니라 절대값으로 둘 수 있습니다. 
$$
\min_{\theta}(Y-X\theta)^T(Y-X\theta) + \lambda||\theta||_1
$$
### Geometric Interpretation
Ridge나 Lasso 모두 결국 다음 목적 함수를 최소화하는 최적화 문제로 볼 수 있습니다. 다만 둘의 차이는 다른 제약사항이 있는 것이지요.
$$
\min_{\theta}(Y-X\theta)^T(Y-X\theta) 
$$
L1-norm(Lasso)의 제약 사항:
$$
||\theta||_1 \le t
$$
L2-norm(Ridge)의 제약 사항:
$$
||\theta||_2 \le t
$$
이를 그림으로 표현하게 되면 아래와 같습니다. 빨간색 선이 움직이면서 목적 함수를 최소화 되는 지점을 찾아야 하는데, 그 지점이 L-1 norm은 사각형의 코너에 L-2 norm은 원의 중간에 위치하게 될 가능성이 높아 보입니다.
![image](https://user-images.githubusercontent.com/11609881/113402180-944d0e00-93df-11eb-8788-d0541d6cb45d.png)
출처: https://en.wikipedia.org/wiki/Lasso_(statistics)
따라서 **L-1 norm을 쓰게 되면 계수들이 sparse representation**으로 되는 특징이 있습니다.

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



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc5NjQxNTcyMCwtMjI5NzA1NTUxLC02ND
EyODA5NDEsLTE0NDE1NDU4MzUsLTU4MjgzMDMxNSwxNzQ0NjA5
MzA3LDM4NTg1NTY4Niw2ODYzODkyNTQsNjQ4OTAxODA3LC02MD
YyMjY0NTMsLTg5NjMwNjc1Myw2NjM5NDgxNjIsMTI5NzI3NjY3
LDEzNDk4MDUzNzMsMTExMDczMzY2MiwxMTQ5NTIwNTg1LC0xNj
U4MjcxMjcsOTM4NDczMzA4XX0=
-->