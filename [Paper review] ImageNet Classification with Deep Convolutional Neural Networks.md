Deep convolutional neural network로 ImageNet 컨테스트에서 좋은 성적을 거둠. 이전 SOTA보다 더 좋다.
구조는 5개의 Convolutional layer로 구성되어 있고, 60백만개의 파라미터와 65만개의 뉴런들이 있음. max-polling layer들도 사용하였고, 3개의 FC layer들과 출력단에 softmax.
Dropout 사용.

# Introduction
MNIST와 같은 쉬운 데이터들은 적은 훈련 데이터 셋만
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTcwNjgwMzE3Nl19
-->