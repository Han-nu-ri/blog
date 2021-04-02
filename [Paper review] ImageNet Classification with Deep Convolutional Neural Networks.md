Deep convolutional neural network로 ImageNet 컨테스트에서 좋은 성적을 거둠. 이전 SOTA보다 더 좋다.
구조는 5개의 Convolutional layer로 구성되어 있고, 60백만개의 파라미터와 65만개의 뉴런들이 있음. max-polling layer들도 사용하였고, 3개의 FC layer들과 출력단에 softmax.
Dropout 사용.

# Introduction
MNIST와 같은 쉬운 데이터들은 적은 훈련 데이터 셋만으로도 좋은 성능을 냅니다.
그러나 현실 데이터들은 다양성이 존재해서, 더 많은 데이터 셋들이 필요합니다.
큰 데이터 셋을 학습하기 위해서는 learning capacity가 커야 합니다. 하지만 사물 인식 task가 굉장히 복잡하다면, 모델들은 우리가 알지 못하는 데이터에 대한 사전 지식이 필요합니다. CNN 타입의 모델들이 데이터의 사전 지식을 포함해주는데, CNN은 자연적인 이미지로부터 강하고 대부분 맞는 가정들(stationarity, locality)을 만들어줍니다. 게다가 같은 크기의 일반적인 Feedforward NN 보다 학습하기 쉽고, 아주 약간 미약한 성능을 보입니다.
CNN이 이런 장점들이 있음에도, 큰 스케일의 높은 해상도를 가지는 이미지들에 적용하기는 비쌉니다. 다행히도 GPU들이 2D Convolution에 꽤 최적화 되어 있기 때문에 많은 부분 해결 되고 있습니다.
본 논문의 contributions은 아래와 같습니다.
1. ILSVRC-2010과 ILSVRC-2012에 사용된 데이터로 CNN 모델을 학습 시켰고, 가장 좋은 성능을 보였습니다.
2. GPU를 활용해서 최적화된 2D Convolution을 작성하였고, CNN을 학습하기 위한 다른 Operation들을 작성하여 공개하였습니다.
3. Training 시간을 줄이고 성능을 높이기 위해 새로운 feature들을 사용하였습니다.
4. Overfitting을 방지하기 위해 dropout 등 효과적인 테크닉들을 사용하였습니다.


The Architecture
![image](https://user-images.githubusercontent.com/11609881/113373871-c68e4980-93a6-11eb-9152-7cb5984df86d.png)
본 논문의 네트워크 구조는 Figure 1과 같습니다. 5개의 Convolution layer와 3개의 FC layer로 구성되어 있습니다. 이 네트워크의 특징들은 아래와 같습니다.

1. ReLU
2. GPU 병렬 처리 
3. Local Response Normalization
ReLU은 그 특성 상
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwODA4NDg2MzVdfQ==
-->