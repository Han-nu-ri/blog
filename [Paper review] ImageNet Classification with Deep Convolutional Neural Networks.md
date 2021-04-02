Alex Krizhevsky, Ilya  Sutskever, G E Hinton이 2012년 ImageNet을 뒤집어놓으신 **ImageNet Classification with Deep Convolutional Neural Networks** 을 읽고 필요한 부분을 남긴 글 입니다. 저자가 Alex라서 **AlexNet**이라고 합니다.

# Abstract
Deep convolutional neural network로 ImageNet 컨테스트에서 좋은 성적을 거둔 모델입니다. 발표 당시 SOTA보다 더 좋은 성능을 냈었습니다.
구조는 5개의 Convolutional layer로 구성되어 있고, 60백만개의 파라미터와 65만개의 뉴런들이 있습니다. max-polling layer들도 사용하였고, 3개의 FC layer들과 출력단에 softmax를 덧대었으며, Dropout 사용 등 Regularization 기법을 활용하였습니다.

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


# Architecture
![image](https://user-images.githubusercontent.com/11609881/113373871-c68e4980-93a6-11eb-9152-7cb5984df86d.png)
본 논문의 네트워크 구조는 Figure 1과 같습니다. 5개의 Convolution layer와 3개의 FC layer로 구성되어 있습니다. 이 네트워크의 특징들은 아래와 같습니다.

1. ReLU
2. GPU 병렬 처리 
3. Local Response Normalization (LRN)
Generalization을 위한 테크닉입니다. 같은 포지션에 위치하는 다른 커널들의 값들을 활용하여 normalize합니다. VGG에서 거의 효과가 없다고 하여, 잘 쓰이고 있지 않는 것 같습니다.
![image](https://user-images.githubusercontent.com/11609881/113378006-dc087100-93b0-11eb-861b-3d058a0aaa69.png)
4. Overlapping Pooling
전통적으로 Pooling layer들은 Pooling할 때 overlap 되지 않게 하는데요. 본 논문에서는 Pooling 시 Stride 보다 Pooling 영역을 크게 설정하여 overlap pooling을 하였습니다.

# Reducing Overfitting
Overfitting을 줄이기 위하여  다음과 같은 방법을 활용하였습니다.

1. Data Augmentation
데이터의 라벨을 유지하면서 이미지를 horizontal reflection하거나, translation하여 많은 데이터를 얻었습니다.
2. Dropout
이 챕터에는 표현되어 있지 않지만, 목적함수에 Weight decay를 활용하였습니다.

# Details of learning
Optimizer는 SGD + Momentum으로, 128 batch size, 0.9 momentum, 0.0005 weight decay로 hyperparameter를 설정하였습니다. 또한 목적 함수에 Weight decay를 더하였는데, 본 논문의 architecture에서는 학습에 있어 중요함을 확인하였습니다. Learning rate의 경우 0.01로 설정하여, 중료 시점 전까지 3번 줄였습니다.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NzYyMzUyODAsLTE3MTc4MDk3MzMsMj
A3NjY1MjI3NCwtMTIxMjU5NjcyOCwtMjAyODEyODQ2NCwxNzYz
MDI4NDEyXX0=
-->