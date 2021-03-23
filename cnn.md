# CNN (Convolutional Neural Network)의 이해
이미지, 영상과 같은 시각적 데이터에 사용되는 CNN (Convolutional Neural Network)에 대한 글입니다. 위키피디아, http://taewan.kim/post/cnn/#fnref:3 블로그와 CS231n (https://cs231n.github.io/convolutional-networks/)를 참고하였음을 밝힙니다.
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
라고 하면, 아래와 같이 움직이면서 convolution 연산을 하는 것 입니다. 이런 특징 matrix를 필터(filter)라고 합니다 (커널(kernel)이라고도 부릅니다).

![Convolution_schematic](https://user-images.githubusercontent.com/11609881/112200801-f2952680-8c52-11eb-9680-04c158410186.gif)
이미지 출처: http://deeplearning.stanford.edu/wiki/index.php/Feature_extraction_using_convolution

일반적인 이미지의 각 픽셀은 RGB로 표현이 됩니다. RGB 색 모형은 빛의 삼원색을 이용하여 색을 표현하는 방식입니다. RGB로 표현된 이미지의 각 픽셀에는 빨간색, 초록색, 파란색 값이 어느 정도로 섞여 있는지 알 수 있습니다. 예를 들어 주황색은 (255,127,0)으로 나타낼 수 있습니다.
RGB로 표현된 이미지는 각 셀에 세가지 값이 있습니다. 높이와 너비가 32 픽셀인 이미지가 있다고 하면, 32 X 32 X 3의 행렬로 표현할 수 있는 것이죠. 이 행렬을 32 X 32 X 1 크기의 R, G, B 행렬로 나눈 것을 채널(Channel)이라고 합니다.
![image](https://user-images.githubusercontent.com/11609881/112203329-c333e900-8c55-11eb-81fe-3555a08def5c.png)
이미지 출처: http://taewan.kim/post/cnn/#fnref:3

이미지가 RGB와 같은 3개의 채널로 구성되어 있다면, 이와 합성곱하는 필터도 3개의 채널로 구성하여 채널 간 합성곱을 한 후 같은 픽셀끼리 더합니다. 그리고 각 픽셀에 같은 bias 값을 더해주죠 (아래 그림에는 표현되어 있지 않습니다). 그 결과 matrix를 Feature Map이라고 부릅니다. Filter로 대변되는 Feature가 Input data의 어디에 위치하는지 알려주기 때문에 Feature Map이라 부르는 듯 합니다.
![image](https://user-images.githubusercontent.com/11609881/112205451-232b8f00-8c58-11eb-82a5-4d6acb2a5333.png)
이미지 출처: http://taewan.kim/post/cnn/#fnref:3

출력의 크기가 입력에 비해 줄어든 것을 볼 수 있습니다. 합성곱 연산 과정을 따라가면, 필터의 크기가 출력의 크기에 영향을 주는 것을 쉽게 알 수 있습니다. 보통 딥러닝은 깊게 쌓으려고 하는데, 쌓으면 쌓을수록 크기가 작아지니 여간 불편합니다. 출력의 크기를 조절할 수 없을까요? 입력의 경계에 무언가 값을 넣어주면 원하는 크기로 조절할 수 있습니다. 이를 패딩(padding)이라고 하는데, 보통 0을 넣어 주어 zero-padding이라고 합니다. CSS의 padding 속성은 안쪽 여백을 의미하는데, 같은 맥락입니다.
이외도 어떤 요소가 출력의 크기에 영향을 줄까요? 필터를 입력에 좌상단에서 움직일 때, 한 칸씩 움직이지 않고 두 칸씩 움직일 수도 있습니다. 이렇게 한번에 움직이는 칸의 수를 stride(보폭)이라고 합니다. 
![image](https://user-images.githubusercontent.com/11609881/112208128-5885ac00-8c5b-11eb-9ff1-0165a5f2b2d1.png)
이미지 출처: https://lycee-europeen-schuman.eu/index.php/word-of-the-week

일반화해서 출력의 크기를 다음과 같이 표현할 수 있습니다. Padding size는 한 쪽의 크기를 의미하므로 2배 해줍니다.
$$
{N-F+2P \over S} + 1, \\ 
N: input \ size \\
F: Filter \ size \\
P: Padding \ size \\
S: Stride
$$

아래 이미지는 입력 이미지에 한 줄 패딩(양쪽에 하므로 두 줄이 됩니다)하고, 보폭(stride)를 2로 하여 하나의 필터와 합성곱을 하고 있는 과정입니다. 채널의 개수가 3개이므로, 필터도 3개의 채널로 구성된 것을 볼 수 있고 마지막에 Bias를 더해주는 것을 볼 수 있습니다 (RF는 Receptive Field로, 필터와 합성곱 중인 X 영역입니다(그림의 파란색 영역)):
$$
\sum_{i=1}^3 RF_{i} * W_{0i}+b_0 \\
$$
![image](https://user-images.githubusercontent.com/11609881/112209149-7dc6ea00-8c5c-11eb-9a89-7be1ecd5be0b.png)
이미지 출처: https://cs231n.github.io/convolutional-networks/

필터를 하나 더 추가하면 아래와 같습니다. 하나만 이해하면 확장하는 건 쉽습니다.
![image](https://user-images.githubusercontent.com/11609881/112212053-dba90100-8c5f-11eb-911f-1005a837fb62.png)
이미지 출처: https://cs231n.github.io/convolutional-networks/

## 이미지의 특징을 학습하기
CNN은 위와 같은 Layer들을 쌓고, 이미지의 특징을 나타내는 필터(커널)들이 Loss를 줄이는 방향으로 업데이트 되며 학습합니다. 일반적인 뉴럴넷의 학습 과정과 같고, 다만 학습할 파라미터가 필터와 필터 별 바이어스라는 것만 인지하면 됩니다. 
당연히 Fully Connected Layer와 비교하여 학습할 파라미터의 개수가 적습니다. 입력 이미지가 32 X 32 X 3 (W X H X C)이고, 크기가 5 X 5인 필터가 10개 있다면 학습할 파라미터의 개수는 몇 개일까요? (5 X 5 X 3(채널의 개수) + 1) X 10(필터의 개수) 입니다.

또한 Layer가 쌓일수록 더 높은 수준의 특징들이 있습니다. Layer가 쌓일수록 입력으로 들어오는 이미지가 초기 이미지의 여러 특징들을 종합한 이미지가 되기 때문으로 생각됩니다.
![image](https://user-images.githubusercontent.com/11609881/112213909-f2e8ee00-8c61-11eb-84a5-cb37b4595c48.png)
이미지 출처: https://hal.archives-ouvertes.fr/hal-02053205/document
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTkxMzg3MzY2Myw0ODczNzQyMzEsLTM3ND
M1OTYwNywxMjIwOTY2Mjk3LC05ODMxOTQyNTMsMTMwMTc5Mjc2
MSwtMTIxNTAyNDg4NSwtMTAyODE2NDQ4MiwtMTM1MDY5ODM5LC
0xOTI5NTA2MDQxLC0xMDQzNTc2MzUzLC0xMDY0NTg0NjYyLC0x
MzQ4NzM3NjIwXX0=
-->