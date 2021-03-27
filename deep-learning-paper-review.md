# Deep learning
본 포스트는 LeCun, Y., Bengio, Y. & Hinton, G. Deep learning. Nature 521, 436–444 (2015) 논문을 간추린 글 입니다.

## Abstract
딥러닝을 다양한 레벨의 추상화와 함께 데이터의 표현을 배울 수 있는 여러가지의 프로세스 레이어로 구성되어 있는 계산 모델을 가능하게 합니다. 이런 방법들은 음성 인식, 시각적 사물 인식, 사물 감지 그리고 많은 다른 도메인의 SOTA를 극적으로 향상 시켰습니다. 딥러닝은 많은 데이터 셋에 있는 뒤얽힌 구조를 역전파 알고리즘을 사용하여 발견합니다. 역전파 알고리즘은 머신이 이 전 레이어의 표현으로부터 각 레이어의 표현을 계산하기 위해 사용되는 내부 파라미터들을 어떻게 변경 시켜야 하는지 알려줍니다. CNN은 이미지들, 비디오, 스피치와 오디오를 가공하는데 큰 발전을 일으켰고, 반면에 RNN은 텍스트나 스피치와 같은 연속적인 데이터에 빛을 발하고 있습니다.


## Introduction
머신러닝 기술은 현대 사회의 많은 측면에서 힘을 보이고 있습니다. 머신러닝 시스템은 이미지 안의 사물을 인식하거나, 스피치를 텍스트로 번역하거나, 사용자의 흥미와 맞는 제품들을 추천하는 등에 사용됩니다. 이런 어플리케이션들은 딥러닝이라 불리는 기술들을 더욱 더 이용하고 있습니다.
보편적인 머신러닝 기술들은 원시 데이터를 가공하는데 제한적이었습니다. 수십년동안, 패턴 인지나 머신러닝 시스템을 구축하는 것은 원시 데이터에서 데이터의 표현을 추출하기 위해 조심스러운 엔지니어링과 도메인 전문가가 필요했습니다.
Representation learning은 머신이 원시 데이터로부터 감지나 분류 작업을 위해 필요한 표현들을 자동으로 발견하는 것을 가능하게 해줍니다. 딥러닝은 간단하지만 비선형인 모듈들을 구성하여 원시 데이터 입력으로부터 시작하는 표현을 조금 더 높은 추상화 레벨로 바꿔주고, 이를 통해 여러 레벨의 표현들을 얻는 Representation learning 방법입니다. 이미지를 예로 들면, 첫 번째 레이어는 이미지에 존재하는 선들을 감지하게 됩니다. 두 번째 레이어는 여러 선들의 배열로부터 감지되는 패턴들을 감지하게 됩니다. 딥러닝의 핵심적인 측면은 이들을 데이터로부터 배운다는 것 입니다.

## Supervised learning
머신러닝의 가장 일반적인 형태는 supervised learning입니다. 우리가 집, 자동차, 사람 혹은 고양이가 담긴 이미지들을 분류하고 싶다고 상상해보죠. 우리는 먼저 라벨링된 데이터들을  모으고, 에러를 측정하는 목적 함수를 줄이는 방향으로 머신의 파라미터들을 조절하도록 훈련 시킵니다.
적절히 파라미터들을 조절하기 위해, 학습 알고리즘은 파라미터가 조금 변할 때 에러가 어떻게 변하는 지를 표현해주는 기울기 벡터를 계산합니다. 목적 함수는 훈련 데이터들로 평균된 파라미터들의 고차원 공간 안의 경사로 볼 수 있고, 음수 기울기 벡터는 목적 함수가 최소점에 가까워지도록 경사 안의 가장 빠르게 떨어지는 방향을 가르킵니다.
일반적으로 Stochastic gradient descent (SGD)라고 불리우는 과정을 사용합니다. SGD는 몇 가지의 데이터들로 입력 벡터들을 구성하고, 출력들과 에러들, 그리고 평균 기울기를 계산하여 파라미터들을 조절합니다. 이 과정을 목적 함수가 줄어드는 것을 멈출 때까지 반복하게 됩니다. Stochastic이라고 불리는 이유는 전체 데이터의 평균 gradient에 대한 noisy estimate을 제공하기 때문입니다.

## Backpropagation
![image](https://user-images.githubusercontent.com/11609881/112597276-4587fd00-8e50-11eb-9ddb-0b4b3066984a.png)
이미지 출처: LeCun, Y., Bengio, Y. & Hinton, G. Deep learning. Nature 521, 436–444 (2015) 

SGD를 통해 Multilayer architecture를 학습 시킬 수 있고, architecture 내 함수들이 상대적으로 smooth한 함수들로 구성되어 있다면 Backpropagation 알고리즘으로 gradient들을 계산할 수 있습니다.
gradient들을 계산하기 위한 Backpropation 과정은 chain rule의 실용적인 application에 불과합니다. 핵심 insight는 objective function의 derivative(gradient)는 upstream gradient와 local gradient를 곱하여 계산할 수 있다는 것 입니다.  Backpropation 과정은 네트워크의 가장 끝에서부터 처음까지 gradient들을 chain rule를 사용하여 반복적으로 계산해나가면 됩니다.

 

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM0NjU5NTg0MSwtMjkxNTQ0MjE4LC0xNz
YyMDM0NDUsLTE0NjA3NjYxODEsMTMzODQxNjE4MCwtMTI0NTcw
MTY0MV19
-->