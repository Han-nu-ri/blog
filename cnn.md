# CNN: (Convolutional Neural Network)의 이해
이미지, 영상과 같은 시각적 데이터에 사용되는 CNN (Convolutional Neural Network)에 대한 글입니다. 위키피디아와 CS231n 강의노트를 참고하였음을 밝힙니다.
## 도입
사람은 이미지, 영상을 어떻게 이해할까요? 깨어 있는 동안 수많은 시각적 정보를 보는데, 그 모든 정보에 중요하게 받아들이지는 않습니다. 산책을 하면서 지나가는 사람들, 나무들을 의식하지 않으면 대부분 인지 과정의 유의미한 신호로 처리 되지 않습니다. 잠시 제 뇌 안에 머물다가 사라지거나,심지어 인식하지도 못하는 것이지요.
![Iu](https://user-images.githubusercontent.com/11609881/111646763-45cb3b80-8845-11eb-8a03-35fb0b8e97c7.gif)
그럼 어떤 정보가 유의미하다는 것을 어떻게 판단할까요? 위 gif를 보시죠. gif를 보면서, 저는 먼저 무언가 움직이고 있음을 인지하고 이것들을 중요한 정보로 판단하였습니다. t의 변화에 따른 그래프의 변화임을 판단하고 어떤 식인지 확인하였습니다. 이런 정보들을 종합적으로 합쳐서 해석하였습니다. 이 글을 쓰면서 자세히 보니, 수학식 왼쪽에 있는 1, 2과 같은 숫자들이 보이네요. 처음 gif를 이해할 때 그다지 유용하지 않다고 판단된 것 같습니다.
사람마다 순서와 방식은 다르겠지만 비슷할 거라고 생각합니다. 시각적 정보를 하나하나 픽셀 단위로 이해하는 것이 아니라, 자연스럽게 학습된 시각적 정보를 이해하기 위한 중요한 특징들을 파악하고 이를 종합해서 판단하는 것이죠.
CNN(Convolutional Neural Network)은 위와 같은 사람의 시각적 정보를 이해하는 방식을 활용하여 모델을 구성합니다. 이미지의 중요한 특징을 학습해서, 새로운 이미지에 학습된 중요한 특징이 있는지 확인하게 됩니다.
## Convolution
CNN에 활용되는 합성곱(Convolution) 연산에 대하여 이해해보죠. 합성곱은 아래 이미지로 굉장히 쉽게 이해할 수 있습니다. 파란색 함수와 빨간색 함수가 있을 때, 빨간색 함수를 반전 시킨 후에 오른쪽으로 이동해가면서 파란색과 빨간색 함수가 겹치는 부분을 적분하는 연산입니다.
![image](https://user-images.githubusercontent.com/11609881/112197016-f7f07200-8c4e-11eb-892a-99f6cffbdeb7.png)
이미지 출처: https://ko.wikipedia.org/wiki/%ED%95%A9%EC%84%B1%EA%B3%B1

## Convolution을 활용한 이미지 특징 찾기
![image](https://user-images.githubusercontent.com/11609881/112199227-49016580-8c51-11eb-8eb0-439fdf84ae49.png)
이미지 출처: https://www.usatoday.com/story/life/music/2017/04/13/john-mayer-search-for-everything-new-album/100372750/

위 이미지에서 눈을 어떻게 찾을 수 있을까요? 눈 모양 matrix를 좌상단에서부터 움직이면서 convolution 연산을 하고, 그 값이 높은 지점들을 찾으면 됩니다.

눈 모양 matrix를 
$$
\begin{bmatrix}
1 & 0 & 1 \\
0 & 1 & 0 \\
1 & 0 & 1 \\
\end{bmatrix}
$$
라고 하면, 아래와 같이 움직이면서 convolution 연산을 하는 것 입니다. 이런 특징 matrix를 filter라고 합니다.

![Convolution_schematic](https://user-images.githubusercontent.com/11609881/112200801-f2952680-8c52-11eb-9680-04c158410186.gif)
이미지 출처: http://deeplearning.stanford.edu/wiki/index.php/Feature_extraction_using_convolution

일반적인 이미지의 각 픽셀은 RGB로 표현이 됩니다. RGB 색 모형은 빛의 삼원색을 이용하여 색을 표현하는 방식입니다. RGB로 표현된 이미지는 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzY2NjU4MTgzLC0xOTI5NTA2MDQxLC0xMD
QzNTc2MzUzLC0xMDY0NTg0NjYyLC0xMzQ4NzM3NjIwXX0=
-->