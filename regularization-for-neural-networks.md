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
forward pass할 때 임의로 몇 뉴런들을 0으로 만듭니다.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI0NTI4MTA1OCwxMzQ5ODA1MzczLDExMT
A3MzM2NjIsMTE0OTUyMDU4NSwtMTY1ODI3MTI3LDkzODQ3MzMw
OF19
-->