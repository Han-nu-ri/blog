# Deep learning
본 포스트는 LeCun, Y., Bengio, Y. & Hinton, G. Deep learning. Nature 521, 436–444 (2015) 논문을 읽고, 남기고 싶은 내용들로 간추린 글 입니다. 

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
1990년 후반에 뉴럴 넷과 Backpropagation은 Computer vision과 speech recognition community에서 무시당했습니다. 그 당시에는 작은 prior knowledge를 통해 유의미한 feature를 추출하는 것이 불가능해보였습니다. 간단한 gradient descent는 local minima에 빠질 수 있다고 생각했었죠.
실제로는 네트워크의 크기가 크면 local minima는 거의 문제가 되지 않습니다. 초기 컨디션과 무관하게, 시스템은 거의 언제나 매우 유사한 품질로 솔루션에 도달하게 됩니다. 

## CNN
CNN은 이미 정리한 포스트가 있어 생략합니다.
https://nrhan.tistory.com/entry/CNN-Convolutional-Neural-Network%EC%9D%98-%EC%9D%B4%ED%95%B4
## Distributed representations and language processing
딥러닝은 distributed representation을 쓰지 않는 전통적인 학습 알고리즘에 비해 큰 장점들이 있습니다. 먼저 학습 기간 때 보였던 feature들 외의 새로운 값의 조합에 대한 generalization입니다.  두 번째로,  딥러닝은 학습 과정에서 입력 안의 explicitly하게 존재하지 않는 semantic feature들을 one-hot vector에서 embedding vector로 변경 시키면서 배울 수 있습니다. NLP Application에서는 이런 단어에 대한  Vector representation을 광범히 활용하고 있습니다.
딥러닝을 활용한 language model 전에는, language에 대한 통계적 모델링의 표준적인 접근 방법은 N-grams이었습니다. N-grams은 길이가 N까지의 연속된 단어 조합이 발생하는 빈도수를 세는 것에 기반합니다. 그렇기 때문에 연속적인 단어들 사이에 semantic을 일반화하지 못합니다.
(distributed representation에 대한 내용은 https://nrhan.tistory.com/entry/distributed-representation 에 포스트하였습니다.)
## RNN
스피치나 언어와 같은 연속적인 입력과 관련된 태스크를 처리하는데 있어, RNN 계열의 딥러닝을 사용하는 것이 좋습니다. RNN은 연속된 입력을 처리하는데, state vector라는 hidden unit들을 포함하고 있습니다. 이 state vector은 입력의 과거 정보들을 implicitly하게 가지고 있습니다.
RNN의 Weight를 학습하기 위해서는 RNN을 unfold한 후 Backpropagation을 하면 됩니다. 다만 다른 step 간 Weight는 공통으로 쓰이고, t 시간의 출력이 이 전 t-1, t-2 시간의 값들에 영향을 받는다는 것을 유의하면 됩니다. (자세한 내용은 잘 정리된 포스트를 공유합니다. https://aikorea.org/blog/rnn-tutorial-3/ )
![image](https://user-images.githubusercontent.com/11609881/112741537-abe05d00-8fc1-11eb-9a7e-cb0ae9d93dc9.png)
이미지 출처: LeCun, Y., Bengio, Y. & Hinton, G. Deep learning. Nature 521, 436–444 (2015) 

RNN은 매우 강력하지만, gradient를 backpropgated하는 과정에서 explode하거나 vanish하는 문제가 있습니다. 이런 문제들은 RNN의 진보된 Architecture로 해결되었습니다.
RNN을 Unfold하면, 같은 Weight를 가지는 매우 깊은 layer들로 구성됨을 알 수 있습니다. RNN의 주 목적은 매우 긴 의존 관계를 배우기 위해서 이지만, 이론적이고 실증적인 증거들이 어렵다는 것을 보이고 있습니다.
이것을 바로 잡기 위한 한 아이디어는 explicit한 메모리를 활용하는 것 입니다. 이런 아이디어를 활용하도록 제안된 첫 번째 모델은 LSTM 네트워크입니다.
## The future of deep learning
비록 이 논문에서는 집중하지 못했지만, Unsupervised learning이 시간이 지날수록 더 중요해질 것으로 기대하고 있습니다. 사람과 동물은 각 세상을 관찰하면서 구조를 발견하는 unsupervised learning을 하기 때문입니다.
컴퓨터 비전에서는 CNN과 RNN을 end-to-end 형태로 합치고, reinforcement learning으로 무언가를 결정하는 시스템을 예상하고 있습니다.
자연어 이해에서는 RNN 계열이 시간에 따라 Selective Attention(**Selective attention** is the process of focusing on a particular object in the environment for a certain period of time.)을 배우는 전략을 사용하면 문장이나 전체 문서를 이해하는데 더 잘할 것으로 예상하고 있습니다.


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5NTk2MTg2MjUsMTE0OTMwOTcyNywtMT
QzNjU5MjE3MCwtMTk4NTEwNywtNjIyNzYxNDEwLDU0Mzg2OTQ4
LDE3Mzk4NDI0MjQsLTIwMTYzMzY4NCw5MjIyMzI3ODgsLTk1OT
AzMjY2MCwtMTA1NjUwMzQxNCw2OTgzNDA0NjIsNDY4NzMzMzI3
LC0xNjEyODkwNTcxLC0yOTE1NDQyMTgsLTE3NjIwMzQ0NSwtMT
Q2MDc2NjE4MSwxMzM4NDE2MTgwLC0xMjQ1NzAxNjQxXX0=
-->