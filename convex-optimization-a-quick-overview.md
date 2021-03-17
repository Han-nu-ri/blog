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

(1-\lambda)x + \lambda y의 의미는, \lambda를 0에서 1로 증가 시키면서 어떻게 값이 변해가는지 관찰하면 쉽게 x에서 y로 이동하는 과정임을 알 수 있습니다.

## 볼록 함수
> 볼록 집합 S 위의 함수 f가 다음을 만족하면 f를 볼록 함수라고 한다.
$$
f((1-\lambda)x + \lambda y) \le (1-\lambda)f(x) +\lambda f(y), \forall x, y \in S, \forall \lambda : 0 \le \lambda \le 1
$$
> -f가 볼록이면 오목, 볼록이면서 오목이면 평면 함수라고 한다.

볼록 함수라는 표현이 있으면 바로 떠올려야 하는 부등식, Jensen's Inequality 입니다.  f((1-\lambda)x + \lambda y)는 아래 점이고, (1-\lambda)f(x) + \lambda f(y)는 위 점입니다. 함수가 볼록하다면 이 부등식이 성립함을 직관적으로 이해할 수 있습니다.
![image](https://user-images.githubusercontent.com/11609881/111483329-0d116080-8778-11eb-95ee-106bdee54b09.png)

## 가능 방향
> 가능해 x에서 y 방향으로 가능성을 유지하며 0 보다 큰 거리를 움직일 수 있을 때 y를 가능 방향이라고 한다.

x가 Feasible region 안에 있을 때 y 방향으로 아주 조금 움직여도 여전히 Feasible region에 있는 경우, y를 가능 방향이라고 합니다. 색칠된 영역을 Feasible region이고 x가 우상단의 점에 있을 때 화살표 방향들이 가능방향이 됩니다.
![image](https://user-images.githubusercontent.com/11609881/111484620-472f3200-8779-11eb-93aa-032f0388a6e9.png)
수학적으로 아래와 같이 표현할 수 있습니다. \overline{\lambda}는 0 보다 큰 아주 작은 값 입니다.
$$
x+\lambda y \in F, \forall \lambda : 0 \le \lambda \le \overline{\lambda}.
$$

## 기울기 벡터
> 함수 f의 \overline{x}에서의 기울기 벡터는
$$
\nabla f(\overline{x})=\begin{bmatrix}
\partial f(\overline{x})\over \partial x_1 \\
\cdots \\
\partial f(\overline{x})\over \partial x_n \\
\end{bmatrix}
$$
>이다.

기울기 벡터는 함수 f 위의 특정 점에서 접선을 긋고, 접선과 수직인 방향으로 진행하는 벡터를 떠오르시면 됩니다. 아래 그림에서의 빨간색 선입니다. 기울기 벡터는 함수의 순간 증가율이 가장 큰 방향입니다.
![image](https://user-images.githubusercontent.com/11609881/111488496-a3e01c00-877c-11eb-983e-35ff4ba896da.png)
## 가능 방향  정리
> x가 볼록 집합 F에서 볼록 미분가능 함수 f의 최소해일 필요충분조건은 x의 모든 가능 방향 y와 
$$
\nabla{f(x)^T}y\ge0
$$
이다.

기울기 벡터는 함수가 순간적으로 최대한 증가하는 방향입니다. 따라서 기울기 벡터와 방향 y간 내적이 0 보다 크면 방향 y는 함수가 증가하는 방향이고, 0 보다 작으면 함수가 감소하는 방향입니다.
다시 위의 그림을 떠올려보죠. x가 (1, 0)일 때 기울기 벡터와 모든 가능 방향의 내적을 해보면 모두 양수임을 알 수 있습니다. 이는 무슨 의미일까요? (1, 0)에서는 제약 조건을 만족하면서 움직이면 함수가 증가한다는 것 입니다. 따라서 (1, 0)은 국지 최소해가 됩니다.
더 나아가 함수 f는 볼록 함수이기 때문에, 국지해는 전역 최적해가 됩니다.
## 따름 정리
> 볼록 최적화의 가능해 F의 내부해가 x가 최적해일 조건은
$$
\nabla f(x)=0
$$
이다.

왼쪽 그림을 보죠. 가능해 F의 어떤 점을 선택해도 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5OTgyNTY2ODcsLTkxMzI3NjY5NywyMj
M2NjcwMDYsLTExMDE0MDYzNDIsNDYzMTA2NDg5LDE5MDc5MjA4
NDMsLTE5MjA3ODE5MjIsNzI0NjEzODIxLC02MTgwMTM4ODMsMT
YxMDIxMDA1MF19
-->