Abstract

statistical language model의 목적은 언어의 단어들의 연속에 대한 결합 확률 함수를 학습하는 것입니다. 이것은 curse of dimensionality 때문에 어렵습니다. 이를 해결하기 위한 전통적인 방법은 n-gram입니다. 본 논문에서는 n-gram 대신 semantically 유사한 문장들을 알 수 있는 distributed representation을 제안합니다. model은 단어의 distributed representation을 배우는 것과 더불어, 단어들의 시퀀스에 대한 확률 함수를 배웁니다.

Introduction

statistical model of language은 이 전 단어들이 주어질 때 다음 단어가 발생할 조건부 확률로 표현됩니다.
![image](https://user-images.githubusercontent.com/11609881/113379600-e4fb4180-93b4-11eb-8349-3127a7e5be21.png)
이는 가까운 단어들이 더 중요하다는 사실을 가지고, 다음과 같이 변형할 수 있습니다.
![image](https://user-images.githubusercontent.com/11609881/113379680-1a079400-93b5-11eb-8a9f-ad748e46e339.png)

훈련 corpus에 없는 n-gram 조합이 생기면 어떻게 할까요? 이를 위해 단어들의 시퀀스들을 generalization하는 것이 필요합니다. n-gram 단어들에서 새로운 단어들을 만들기 위해 interpolated n-gram이나 back-off n-gram algorithm이 제안되었습니다.

하지만 이런 generalization 기법에는 하나 혹은 두개 단어 정도 떨어진 context는 중요하게 생각하지 않았고, 단어들간 유사도를 중요하게 생각하지 않은 문제점들이 있었습니다.

이를 해결하기 위해 제안된 아이디어는 다음과 같이 요약할 수 있습니다:
1. 단어들을 distributed된 word feature vector로 표현합니다.
2. 문장의 단어들의 feature vector들의 결합 확률 함수로 단어의 시퀀스를 표현합니다.
3. feature vector와 확률 함수의 파라미터들을 동시에 학습합니다.

Architecture
Training set은 Vocabulary set V 안에 있는 단어들의 시퀀스입니다. 모델의 목적은 t부터 t-n+1까지의 단어들을 입력으로 넣었을 때 t번째 단어가 나올 조건부 확률이 높게 나오도록 만드는 것 입니다.
![image](https://user-images.githubusercontent.com/11609881/113380955-a1a2d200-93b8-11eb-88b2-85f0a6e1ea25.png)
본 논문의 모델에서는 위 함수를 C와 g 두 부분으로 분리합니다:

1. V의 i번째 요소(i번째 단어)를 m dimensional vector(feature vector)로 mapping하는 함수 C. C는 |V| X m matrix로 구성되는데, 각 요소들은 학습 과정에서 업데이트될 distributed representation입니다.
2. feature vector들을 t번째 다음 단어를 위한 조건부 확률 분포와 mapping 시켜주는 함수 g.
![image](https://user-images.githubusercontent.com/11609881/113381211-589f4d80-93b9-11eb-8dc8-ce3eaaaa2259.png)

![image](https://user-images.githubusercontent.com/11609881/113381336-a916ab00-93b9-11eb-82d8-9ac9507aac9d.png)

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM3MjQ0ODQzMSwyMDU2NDY1MzQyLC0yMj
g1NTAyNjYsLTEwMDQ3OTg5NiwtMTE1MjAzNDM1OV19
-->