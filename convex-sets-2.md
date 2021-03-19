# convex-sets-2: 평면 집합, 평면 덮개
평면 집합과 평면 덮개에 관한 포스트입니다. 서울대 홍성필 교수님의 최적화 원론 강의와 https://ratsgo.github.io/linear%20algebra/2017/05/20/spaces/ 블로그 내용을 정리했음을 밝힙니다.
## 평면 집합 (affine set)
l![image](https://user-images.githubusercontent.com/11609881/111723665-43013280-88a7-11eb-93f6-2cf77daab4f4.png)
위는 x1과 x2를 이은 직선에 관한 식과 그림입니다. 직선에서 임의의 두 점을 선택하고, 선택된 두 점을 지나는 직선을 그어보세요. 같은 직선이 그어집니다.
집합 L이 자신의 서로 다른 두 점을 지나는 직선을 항상 포함할 때, L을 평면 집합(affine set)이라고 합니다. 다시 말해 평면 조합에 대하여 닫혀 있는 집합을 평면 집합이라고 합니다. 어떤 연산에 대하여 '닫혀 있다'는 것은, 집합의 임의의 원소들로 연산을 수행한 결과가 같은 집합에 속해 있다는 뜻 입니다.
$$
(1-\lambda)x + \lambda y \in L, \forall x, y \in L, \forall \lambda \in R.
$$

> R^n의 부분 공간은 평면 집합이다. 역은 성립하지 않는다.

R^n의 부분 공간의 예입니다. 사람이 쉽게 생각할 수 있는 3차원을 떠올려보면, 원점을 지나는 부분 공간은 2차원의 무한히 펼쳐진 평면입니다. 따라서 이 평면 위의 평면 조합은 항상 평면 위에 있습니다. 즉 평면 조합에 닫혀 있습니다.
![image](https://user-images.githubusercontent.com/11609881/111732585-266df600-88b9-11eb-89c5-2b8a92f9a222.png)
![image](https://user-images.githubusercontent.com/11609881/111732660-574e2b00-88b9-11eb-91d0-016e0954a12e.png)
(이미지 출처: https://ratsgo.github.io/linear%20algebra/2017/05/20/spaces/)

위 명제의 역은 어떨까요? 아래 직선 L은 평면 집합입니다. 그렇지만 원점을 지나지도, 벡터의 덧셈에 대하여 닫혀 있지도 않으므로 부분 집합이 아닙니다. 따라서 역은 성립하지 않음을 알 수 있습니다.
![image](https://user-images.githubusercontent.com/11609881/111732682-659c4700-88b9-11eb-82be-1d3950e3bbb3.png)
(이미지 출처: https://ratsgo.github.io/linear%20algebra/2017/05/20/spaces/)

부분 공간에 대한 설명은 https://ratsgo.github.io/linear%20algebra/2017/05/20/spaces/ 에 포스트에 잘 설명 되어 있으니 참고하시면 좋을 것 같습니다.

볼록 조합에서 유한 개의 벡터들로 확장한 것처럼, 평면 조합도 유한 개의 벡터들로 다음과 같이 확장할 수 있습니다. 다른 점은 \lambda에 대한 비음 조건이 없다는 것 입니다.
$$
\lambda_1 v_1+\cdots+\lambda_k v_k, \lambda_1+\cdots+\lambda_k=1
$$

## 평면 덮개 (affine hull)
> 집합 S를 포함하는 가장 작은 평면 집합을 S의 평면 덮개 (affine hull)이라고 하고 aff.S로 표기한다.

'가장 작은 평면 집합'이라는 의미는 무엇일까요? 집합 S의 모든 평면 집합의 교집합입니다. 예를 들어보죠. 점 x1, x2가 집합 S에 속할 때
![image](https://user-images.githubusercontent.com/11609881/111723665-43013280-88a7-11eb-93f6-2cf77daab4f4.png)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4NDU1MzMxMDcsLTE0MTAyNTQ2OCwtNj
Y2NDc3MDQyLDIwNjkzMDY0NzIsLTQ4NjUzOTc4OCwtMTc4MTk2
NjQ2MSwxMDc1NzY1NjU0LDIwNDMzODAyNDJdfQ==
-->