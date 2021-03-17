# Convex optimization - a quick overview
볼록최적화의 각론에 들어가기 앞서, 볼록최적화와 관련된 여러 주제들을 다루는 글 입니다. 서울대 홍성필 교수님 최적화 원론 강의를 정리했음을 밝힙니다.
## 볼록 집합
> 집합 S가 자신의 임의의 두 점을 잇는 선분을 포함하면 볼록 집합이라고 한다:
$$
(1-\lambda)x + \lambda y \in S, \forall x, y \in S, \forall \lambda: 0 \le \lambda \le 1.
$$

아래 그림의 왼쪽 두 도형을 보죠. 색이 채워진 도형 안의 임의의 두 점을 잡습니다. 그 두 점을 이은 선 위의 점들은 도형 안에 있나요? 그렇다면 이 도형 안의 점들을 원소로 가지는 집합을 볼록 집합이라고 합니다.

오른쪽 두 도형 안의 점들을 원소로 하는 집합은 볼록 집합일까요?
![convex-optimization-a-quick-overview-1](https://user-images.githubusercontent.com/11609881/111481579-74c6ac00-8776-11eb-9104-6663accecb01.PNG)

## 볼록 함수
> 볼록 집합 S 위의 함수 f가 다음을 만족하면 f를 볼록 함수라고 한다.
$$
f((1-\lambda)x + \lambda y) \le (1-\lambda)f(x) +\lambda f(y), 
$$
> -f가 볼록이면 오목, 볼록이면서 오목이면 평면 함수라고 한다.
## 가능방향  정리
> x가 볼록 집합 F에서 볼록 미분가능 함수 f의 최소해해일 필요충분조건은 x의 모든 가능방향 y와 
$$
\nabla{f(x)^T}y\ge0
$$
이다.


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg2NjY3Nzg3Nyw0NjMxMDY0ODksMTkwNz
kyMDg0MywtMTkyMDc4MTkyMiw3MjQ2MTM4MjEsLTYxODAxMzg4
MywxNjEwMjEwMDUwXX0=
-->