# Regularization
Regularization은 머신러닝에서 굉장히 중요한 주제입니다. 
우리가 어떤 데이터에 대하여 모델을 fitting 시키는데, general한 trend에 fitting 시킬수록 좋습니다. Overfitting은 학습 데이터의 노이즈가 있을 때, 이 노이즈까지 fitting하는 것을 말합니다. 모델이 불필요하게 복잡하다면 Overfitting의 증거일 수 있습니다.

이것을 방지하기 위해 도입하는 개념이 Regularization입니다. 보통 목적 함수에 penalty항을 더하여, 모델이 불필요하게 복잡해지는 것을 막아줍니다.

### Ridge Regression
Linear Regression의 목적 함수에 아래와 같은 계수의 제곱을 더하게 됩니다.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTczMzYyMTQ2NywxMTQ5NTIwNTg1LC0xNj
U4MjcxMjcsOTM4NDczMzA4XX0=
-->