Abstract

statistical language model의 목적은 언어의 단어들의 연속에 대한 결합 확률 함수를 학습하는 것입니다. 이것은 curse of dimensionality 때문에 어렵습니다. 이를 해결하기 위한 전통적인 방법은 n-gram입니다. 본 논문에서는 n-gram 대신 semantically 유사한 문장들을 알 수 있는 distributed representation을 제안합니다. model은 단어의 distributed representation을 배우는 것과 더불어, 단어들의 시퀀스에 대한 확률 함수를 배웁니다.

Introduction

statistical model of language은 이 전 단어들이 주어질 때 다음 단어가 발생할 조건부 확률로 표현됩니다.
![image](https://user-images.githubusercontent.com/11609881/113379600-e4fb4180-93b4-11eb-8349-3127a7e5be21.png)
이는 가까운 단어들이 더 중요하다는 사실을 가지고, 다음과 같이 변형할 수 있습니다.
![image](https://user-images.githubusercontent.com/11609881/113379680-1a079400-93b5-11eb-8a9f-ad748e46e339.png)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwMDQ3OTg5NiwtMTE1MjAzNDM1OV19
-->