# Distributed representation
Distributed representation에 관한 포스트입니다. 

## Representation in deep learning
Representation은 뉴로사이언스, 인지 과학에서의 representation은 현실 세계의 특정한 사물이나 정보를 만들기 위한 사람 마음 안의 심볼을 의미한다고 합니다(https://en.wikipedia.org/wiki/Mental_representation). 굉장히 추상적인데, 저는 사람이 무언가를 떠올릴 때 살아가면서 학습한 그 무언가에 대한 특징들을 무의식적으로 활용한다는 뜻으로 이해했습니다.
딥러닝을 공부하다 보면 representation이라는 단어가 많이 나오는데요, 사람처럼 딥러닝도 무언가를 기억하기 위해 그 무언가에 대한 특징을 학습하기 때문이라고 생각합니다.
> Representation learning은 머신이 원시 데이터로부터 감지나 분류 작업을 위해 필요한 표현들을 자동으로 발견하는 것을 가능하게 해줍니다. 딥러닝은 간단하지만 비선형인 모듈들을 구성하여 원시 데이터 입력으로부터 시작하는 표현을 조금 더 높은 추상화 레벨로 바꿔주고, 이를 통해 여러 레벨의 표현들을 얻는 Representation learning 방법입니다. 이미지를 예로 들면, 첫 번째 레이어는 이미지에 존재하는 선들을 감지하게 됩니다. 두 번째 레이어는 여러 선들의 배열로부터 감지되는 패턴들을 감지하게 됩니다. 딥러닝의 핵심적인 측면은 이들을 데이터로부터 배운다는 것 입니다.

예전에는 학습을 위해 데이터의 feature들을 조심스럽게 추출하고 골랐다면 (feature engineering), 이제는 딥러닝을 통해 이를 자동적으로 (representation learning) 하고 있습니다.
## Local representation
Local representation은 특정한 feature를 표현하는 정보가 대응되는 소규모의 뉴런들에만 존재함을 의미합니다. one-hot encoding은 local representation의 쉬운 예입니다. 예를 들어 아래 단어들을 one-hot encoding으로 표현해보죠.

> 텐서플로
> 고양이

{텐서플로, 딥러닝, 고양이, 강아지}이 4개의 단어가 우리가 관심 있는 단어 셋이라고 하면,

> 텐서플로: {1, 0, 0, 0}
> 고양이: {0, 0, 1, 0}

와 같이 표현될 수 있습니다.
텐서플로라는 단어가 있음을 표현하기 위해서, 첫 번째 비트에 1을 넣는 것 외에는 할 일이 없습니다. 다른 단어들도 마찬가지이지요.

이렇게 특정한 정보를 표현함에 있어 하나의 (혹은 소규모의) 뉴런들만 사용된다면 이를 Local representation이라고 합니다. 만약 우리가 관심 있는 단어 셋이 1000개라고 해보죠. 텐서플로에 해당하는 차원 빼고는 one-hoe encoding 벡터에 많은 요소들이 0이 될 것 입니다. 그래서 one-hot 벡터를 sparce vector라고도 부르게 됩니다.

## Distributed representation
Distributed representation은 정보를 여러 뉴런들의 집합을 통해 표현하는 방법으로, 각 정보는 여러 뉴런들의 활성화로 표현되며 각 뉴런들은 여러 정보들의 representation에 참여하게 됩니다.
{텐서플로, 딥러닝, 프로젝트, 머신러닝} 이 예제로 돌아가보죠. 각 단어를 one-hot encoding의 형태로 표현하기 위해 4차원의 벡터를 사용하였습니다.

이 예제를 distributed representation으로 표현해보죠.
> {}: 000
> {텐서플로}: 001
> {텐서플로, 딥러닝}: 010
> 텐서플로

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExMDUwMDYzNzYsLTc3NjQ4MTk3LDE2NT
U2ODQ3NTksLTEyMzI5NDcwMDYsMTUxNjc3MzUyOSw2NTYxMjQ1
MTEsMTQwNjg1MjY4Nl19
-->